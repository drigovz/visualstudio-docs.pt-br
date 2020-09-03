---
title: Depuração de soluções do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d83c8ffd4fe5ebb627b70fa07f010bdc713225dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72984486"
---
# <a name="debug-sharepoint-solutions"></a>Depurar soluções do SharePoint
  Você pode depurar soluções do SharePoint usando o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador. Quando você inicia a depuração, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o implanta os arquivos de projeto no servidor do SharePoint e, em seguida, abre uma instância do site do SharePoint no navegador da Web. As seções a seguir explicam como depurar aplicativos do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Habilitar depuração](#enable-debugging)

- [Processo de depuração e implantação F5](#f5-debug-and-deployment-process)

- [Recursos do projeto do SharePoint](#sharepoint-project-features)

- [Depurar fluxos de trabalho](#debug-workflows)

- [Depurar receptores de evento de recurso](#debug-feature-event-receivers)

- [Habilitar informações de depuração de Ehanced](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Habilitar depuração
 Quando você depura uma solução do SharePoint pela primeira vez no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , uma caixa de diálogo alertará que o arquivo de web.config não está configurado para habilitar a depuração. (O arquivo de web.config é criado quando você instala o SharePoint Server. Para obter mais informações, consulte [trabalhando com arquivos de Web.config](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)).) A caixa de diálogo oferece a opção de executar o projeto sem Depurar ou modificar o arquivo de web.config para habilitar a depuração. Se você escolher a primeira opção, o projeto será executado normalmente. Se você escolher a segunda opção, o arquivo de web.config será configurado para:

- Ativar a pilha de chamadas ( `CallStack="true"` )

- Desabilitar erros personalizados em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="Off" />` )

- Habilitar depuração de compilação ( `<compilation debug="true">` )

  Segue o arquivo web.config resultante:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 Para reverter as alterações e desabilitar a depuração, altere o seguinte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] no arquivo de web.config:

- Desligar a pilha de chamadas ( `CallStack="false"` )

- Habilitar erros personalizados em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="On" />` )

- Desabilitar depuração de compilação ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>Processo de depuração e implantação F5
 Quando você executa o projeto do SharePoint no modo de depuração, o processo de implantação do SharePoint executa as seguintes tarefas:

1. Executa os comandos de pré-implantação personalizáveis.

2. Cria um arquivo de pacote de solução da Web (. wsp) usando [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comandos. O arquivo. wsp inclui todos os arquivos e recursos necessários. Para obter mais informações, consulte [visão geral de soluções](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Se a solução do SharePoint for uma solução de farm, o reciclará o [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool de aplicativos para o site especificado [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] . Esta etapa libera arquivos bloqueados pelo [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo de trabalho.

4. Se uma versão anterior do pacote já existir, o cancela a versão anterior dos recursos e dos arquivos no arquivo. wsp. Esta etapa desativa os recursos, desinstala o pacote de solução e, em seguida, exclui o pacote de solução no servidor do SharePoint.

5. Instala a versão atual dos recursos e dos arquivos no arquivo. wsp. Esta etapa adiciona e instala a solução no servidor do SharePoint.

6. Para fluxos de trabalho, o instala o assembly de fluxo de trabalho. Você pode alterar seu local usando a propriedade *local do assembly* .

7. Ativa o recurso do projeto no SharePoint se o escopo for site ou Web. Os recursos no farm e os escopos do WebApplication não estão ativados.

8. Para fluxos de trabalho, o associa o fluxo de trabalho à biblioteca do SharePoint, à lista ou ao site que você selecionou no **Assistente para personalização do SharePoint**.

   > [!NOTE]
   > Essa associação ocorre somente se você selecionou **associar automaticamente o fluxo de trabalho** no assistente.

9. Executa os comandos pós-implantação personalizáveis.

10. Anexa o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador ao [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] processo (*w3wp.exe*). Se o tipo de projeto permitir que você altere a propriedade de *solução de área restrita* e seu valor for definido como **true**, o depurador será anexado a um processo diferente (*SPUCWorkerProcess.exe*). Para obter mais informações, consulte [Considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).

11. Inicia o depurador do JavaScript se a solução do SharePoint for uma solução de farm.

12. Exibe a biblioteca, a lista ou a página apropriada do site no navegador da Web.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] exibe uma mensagem de status na janela de saída após a conclusão de cada tarefa. Se uma tarefa não puder ser concluída, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o exibirá uma mensagem de erro na janela lista de erros.

## <a name="sharepoint-project-features"></a>Recursos do projeto do SharePoint
 Um recurso é uma unidade de funcionalidade portátil e modular que simplifica a modificação de sites usando definições de site. Ele também é um pacote de [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] elementos (WSS) que pode ser ativado para um escopo específico e que ajuda os usuários a realizar uma determinada meta ou tarefa. Os modelos são implantados como recursos.

 Quando você executa um projeto no modo de depuração, o processo de implantação cria uma pasta no diretório de *recursos* em *%COMMONPROGRAMFILES%\Microsoft Shared\Web Server Extensions\14\TEMPLATE\FEATURES*. Os nomes de recursos têm o formato *nome do projeto*_Feature*x*, como TestProject_Feature1.

 A pasta da solução no diretório de recursos contém um arquivo de *definição de recurso* e um arquivo de definição de *fluxo de trabalho* . O arquivo de definição de recurso (Feature.xml) descreve os arquivos no recurso do projeto. o arquivo de definição de projeto (*Elements.xml*) descreve o modelo de projeto. *Elements.xml* pode ser encontrado em **Gerenciador de Soluções**, mas Feature.xml é gerado quando o pacote de solução é criado. Para obter mais informações sobre esses arquivos, consulte [projeto do SharePoint e modelos de item de projeto](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Depurar fluxos de trabalho
 Quando você depura projetos de fluxo de trabalho, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o adiciona o modelo de fluxo de trabalho (dependendo de seu tipo) a uma biblioteca ou a uma lista. Em seguida, você pode iniciar o modelo de fluxo de trabalho manualmente ou adicionando ou atualizando um item. Você pode usar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o para depurar o fluxo de trabalho.

> [!NOTE]
> Se você adicionar referências a outros assemblies, verifique se esses assemblies estão instalados no cache de assembly global ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). Caso contrário, a solução de fluxo de trabalho falhará. Para obter informações sobre como instalar assemblies, consulte [iniciar manualmente um fluxo de trabalho em um documento ou item](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 No entanto, o processo de implantação não inicia o fluxo de trabalho. Você deve iniciar o fluxo de trabalho no site do SharePoint. Você também pode iniciar o fluxo de trabalho usando um aplicativo cliente, como Microsoft Office Word 2010, ou usando um código separado do lado do servidor. Use uma das abordagens especificadas no **Assistente para personalização do SharePoint**.

 Por exemplo, se você especificou que o fluxo de trabalho pode ser iniciado manualmente, inicie o fluxo de trabalho diretamente do item na biblioteca ou lista. Para obter mais informações sobre como iniciar um fluxo de trabalho manualmente, consulte [iniciar manualmente um fluxo de trabalho em um item de documento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Depurar receptores de evento de recurso
 Por padrão, quando você executa um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplicativo do SharePoint, seus recursos são automaticamente ativados para você no servidor do SharePoint. No entanto, isso causa problemas quando você depura receptores de evento de recurso, porque quando um recurso é ativado pelo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ele é executado em um processo diferente do depurador. Isso significa que algumas funcionalidades de depuração, como pontos de interrupção, não funcionarão corretamente.

 Para desabilitar a ativação automática do recurso no SharePoint e permitir a depuração adequada de receptores de evento de recurso, defina o valor da propriedade de **configuração de implantação ativa** do projeto como **sem ativação** antes da depuração. Em seguida, depois de começar a depurar seu aplicativo do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ative manualmente o recurso no SharePoint. Para ativar o recurso, abra o **menu ações do site** no SharePoint, escolha configurações do **site**, escolha o link **gerenciar recursos do site** e, em seguida, escolha o botão **Ativar** ao lado do recurso para continuar a depuração normalmente.

## <a name="enable-enhanced-debugging-information"></a>Habilitar informações de depuração avançadas
 Devido às vezes, as interações complexas entre o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processo (devenv.exe), o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processo de host do SharePoint (*vssphost4.exe*), o SharePoint e a camada do WCF, o diagnóstico de erros que ocorrem durante a criação, implantação e assim por diante pode ser um desafio. Para ajudá-lo a resolver esses erros, você pode habilitar informações de depuração avançadas. Para fazer isso, vá para a seguinte chave do registro no registro do Windows:

 **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Se o valor de **REG_DWORD** "EnableDiagnostics" ainda não existir, crie-o manualmente. Defina o valor "EnableDiagnostics" como "1".

 Definir esse valor de chave como 1 faz com que as informações de rastreamento de pilha apareçam na janela de **saída** sempre que os erros do sistema de projeto ocorrerem enquanto você estiver executando o no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para desabilitar as informações de depuração avançadas, defina EnableDiagnostics de volta como 0 ou exclua o valor.

 Para obter mais informações sobre outras chaves do registro do SharePoint, consulte [extensões de depuração para as ferramentas do SharePoint no Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Confira também
- [Solucionar problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)
