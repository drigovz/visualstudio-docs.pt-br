---
title: Solução de problemas de soluções do SharePoint | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e8ccaaf877c04b3d58fc6d54bb658c2cef77b6f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985308"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Solucionar problemas de soluções do SharePoint
  Os seguintes problemas ou alertas podem ocorrer quando você depura soluções do SharePoint usando o depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, consulte [Depurando soluções de fluxo de trabalho do SharePoint 2007](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrições de token em Web Parts visuais em área restrita
 As Web Parts visuais em soluções de área restrita não podem processar tokens padrão, como $SPUrl, que o tempo de execução do SharePoint dá suporte. Como resultado, a URL não será resolvida e você não poderá visualizar o conteúdo em modo de exibição de Design no designer de Web Part Visual se fizer referência a ele diretamente em um elemento de script, como no exemplo a seguir:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Para contornar essa limitação e resolver o token, consulte-o usando literais:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restrições de caracteres em nomes de projetos e itens de projeto
 Os nomes de projetos e itens de projeto só podem conter caracteres válidos em um caminho de implantação no SharePoint 2010. Nenhum outro caractere é permitido.

### <a name="error-message"></a>Mensagem de erro
 Mensagem de erro "caracteres inválidos".

### <a name="resolution"></a>Resolução
 Para nomes de projetos do SharePoint e itens de projeto, use apenas os seguintes caracteres:

- Caracteres ASCII alfanuméricos

- Espaço

- Ponto final (.)

- Vírgula (,)

- Sublinhado (_)

- Dash (-)

- Barra invertida (\\)

  Quando um projeto é empacotado, uma regra de validação verifica se a propriedade do caminho de implantação para cada arquivo que você está implantando contém apenas esses caracteres válidos.

## <a name="errors-when-creating-custom-fields"></a>Erros ao criar campos personalizados
 No [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], os campos personalizados são definidos em XML. Poderão ocorrer erros se um campo não for definido ou referenciado usando um formato específico.

### <a name="error-message"></a>Mensagem de erro
 Mensagem de erro "caracteres inválidos" no momento do empacotamento.

### <a name="resolution"></a>Resolução
 A ID de uma definição de campo deve ser um GUID entre chaves, como mostra o exemplo a seguir:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Como mostra o exemplo a seguir, uma referência de campo em um tipo de conteúdo deve ser definida usando o formato de elemento vazio (\<FieldRef/>), não usando elementos de início/término (\<FieldRef >\</FieldRef >):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Se o XML de origem do campo estiver malformado, não for um arquivo XML válido ou apresentar algum outro problema, ocorrerá o erro "não é possível analisar o arquivo".

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Novas definições de site que não são do inglês não aparecem na página de criação do site após a implantação
 Depois de criar e implantar uma definição de site usando uma versão diferente do inglês do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (ou seja, uma versão com uma localidade [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] diferente de 1033), a guia **personalizações do SharePoint** não aparecerá na caixa de **seleção de modelo** e no novo site o modelo não aparece na página **novo site do SharePoint** .

### <a name="error-message"></a>Mensagem de erro
 nenhuma.

### <a name="resolution"></a>Resolução
 Esse problema ocorre devido a um valor incorreto na propriedade **path** para o arquivo de configuração de definição de site do WebTemp, como *webtemp_SiteDefinitionProject1. xml*. Na propriedade **path** do arquivo WebTemp, localizado no **local de implantação**, altere 1033 para a localidade apropriada [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por exemplo, para usar uma localidade japonesa, altere o valor para 1041. Para obter mais informações, consulte [IDs de localidade atribuídas pela Microsoft](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>O erro aparece quando um projeto de fluxo de trabalho é implantado em um sistema limpo
 Esse problema ocorre se você implantar um projeto de fluxo de trabalho no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] em um sistema limpo. Um sistema limpo é um computador que tem uma nova instalação do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e do SharePoint, mas nenhum projeto de fluxo de trabalho implantado.

### <a name="error-message"></a>Mensagem de erro
 Não é possível localizar a lista do SharePoint: histórico de fluxo de trabalho.

### <a name="resolution"></a>Resolução
 Esse erro ocorre devido a uma lista de histórico de fluxo de trabalho ausente. Como o ambiente de desenvolvimento é um sistema limpo, nenhum fluxo de trabalho é implantado e a lista de histórico de fluxo de trabalho ainda não existe. Para resolver esse problema, abra novamente o assistente de fluxo de trabalho, que faz com que a lista de histórico do fluxo de trabalho seja criada.

##### <a name="to-reenter-the-workflow-wizard"></a>Para inserir novamente o assistente de fluxo de trabalho

1. Em **Gerenciador de soluções**, escolha o nó do fluxo de trabalho.

2. Na janela **Propriedades** , escolha o botão de reticências (...) em qualquer propriedade que tenha um botão de reticências.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>O usuário deve atualizar a página do aplicativo no navegador durante a depuração para exibir a imagem atualizada
 Se você estiver Depurando uma solução do SharePoint que contém uma página de aplicativo com um controle que exibe uma imagem, como um controle de imagem [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)], você deverá atualizar a página no navegador para exibir as alterações feitas na imagem.

## <a name="error-the-site-location-is-not-valid"></a>Erro: o local do site não é válido
 Esse problema pode ocorrer se o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] não estiver instalado. Isso também pode ocorrer se você não tiver acesso de administrador ao site do SharePoint especificado no **Assistente para personalização do SharePoint**.

### <a name="error-message"></a>Mensagem de erro

- O local do site do SharePoint não é válido.

### <a name="resolution"></a>Resolução

- Instale o Console do [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Verifique se você tem acesso de administrador ao site do SharePoint. Para obter mais informações, consulte o artigo [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] online [atribuir ou remover administradores de aplicativos de serviço no SharePoint Server](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>O evento Web de exclusão de site não ocorre no projeto receptor de eventos
 Quando você cria um projeto receptor de eventos e seleciona determinados eventos da Web, como "um site está sendo excluído", o evento nunca ocorre.

### <a name="error-message"></a>Mensagem de erro
 nenhuma.

### <a name="resolution"></a>Resolução
 Esse problema ocorre porque o escopo do recurso deve ser "site" para lidar com eventos no nível do site, mas o escopo do recurso padrão para projetos receptores de eventos é "Web". Os eventos da Web afetados são:

- Um site está sendo excluído (webexcluindo)

- Um site foi excluído (webdeled)

- Um site está sendo movido (webmovendo)

- Um site foi movido (removida)

  Para corrigir o problema, altere o escopo do recurso do receptor de evento, da seguinte maneira.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Para alterar o escopo do recurso do receptor de eventos

1. No **Gerenciador de soluções**, abra o arquivo *. Feature* do receptor de eventos no **Designer de recursos** clicando duas vezes no arquivo ou abrindo o menu de atalho e escolhendo **abrir**.

2. Escolha a seta ao lado de **escopo**e escolha **site** na lista exibida.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>O erro de implantação aparece depois que o nome de um identificador em um projeto de modelo de conectividade de dados corporativos é alterado
 Esse problema ocorre se você alterar o nome do identificador de uma entidade em um modelo de BDC (conectividade de dados corporativos) e, em seguida, tentar implantar a solução.

### <a name="error-messages"></a>Mensagens de erro

- o *nome do modelo*de \<> tem os seguintes erros de ativação de tipo de conteúdo externo...

- O IMetadataObject com o nome '\<*Model name*> ' tem um valor no campo ' name ' que está duplicado...

### <a name="resolution"></a>Resolução
 Para resolver esse problema, exclua o modelo manualmente e, em seguida, implante a solução novamente.  Você pode excluir o modelo usando uma das seguintes ferramentas:

- Administração Central do SharePoint 2010. Para obter mais informações, consulte [BDC gerenciamento de modelos](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#deleteamodel) no site do Microsoft TechNet.

- Windows PowerShell. Você pode excluir o modelo digitando este comando no prompt de comando: **Remove-SPBusinessDataCatalogModel**. Para obter mais informações, consulte [cmdlets gerais (SharePoint Server 2010)](/powershell/module/sharepoint-server/&view=sharepoint-ps) no site do Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Um erro é exibido quando você tenta exibir uma Web Part Visual no SharePoint
 Esse problema ocorre quando a propriedade **path** do controle de usuário não começa com a cadeia de caracteres "controltemplates\\".

### <a name="error-messages"></a>Mensagens de erro

- O arquivo '/_CONTROLTEMPLATES/ *\<nome do projeto >* / *\<nome da Web Part >* /\<*nome do controle de usuário >* . ascx ' não existe.

- Erro de servidor no aplicativo '/'.

### <a name="resolution"></a>Resolução

##### <a name="to-resolve-this-issue"></a>Para resolver esse problema

1. Em **Gerenciador de soluções**, escolha o arquivo de controle de usuário, cuja extensão de nome de arquivo é *. ascx*.

2. Na barra de menus, escolha **exibir** > **janela Propriedades**.

3. Na janela **Propriedades** , expanda o nó **local de implantação** .

4. Verifique se o valor da propriedade **path** começa com a cadeia de caracteres "controltemplates\\".

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>O erro aparece quando um fluxo de trabalho reutilizável importado que contém um campo de formulário de tarefa é executado
 Esse problema ocorrerá se você importar um fluxo de trabalho que contém um formulário de tarefas que tem um campo e, em seguida, executar o novo fluxo de trabalho no mesmo sistema do qual você o importou.

### <a name="error-message"></a>Mensagem de erro
 Ocorreu um erro na etapa de implantação ' ativar recursos ': o campo com ID [*GUID*] definido no recurso [*GUID*] foi encontrado no conjunto de sites atual ou em um subsite.

### <a name="resolution"></a>Resolução
 Esse erro é o resultado de colisões de ID de campo que ocorrem porque o projeto de fluxo de trabalho reutilizável de importação no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] não altera as IDs de campo de formulário de tarefa. Se você implantar um fluxo de trabalho importado no mesmo servidor que contém o fluxo de trabalho original, ocorrerão colisões de ID de campo.

 Para resolver esse problema, use o recurso Localizar e substituir para alterar o valor do atributo ID de campo em todos os arquivos de fluxo de trabalho importados.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>O erro aparece quando uma instância de lista importada renomeada é executada
 Esse problema ocorre se você renomear uma instância de lista importada e executá-la em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

### <a name="error-message"></a>Mensagem de erro
 Erro de compilação: ocorreu um erro na etapa de implantação ' ativar recursos ': o arquivo Template\Features\\[*nome*do<em>recurso</em>de*projeto de importação*] \Files\Lists\\[<em>nome da lista</em>*antiga*] \Schema.xml não existe.

### <a name="resolution"></a>Resolução
 Quando você importa uma instância de lista, um atributo chamado CustomSchema é adicionado ao arquivo elements. XML da instância da lista. Elements. XML inclui o caminho de um Schema. xml personalizado para a instância de lista. Quando você renomeia a instância de lista no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], o caminho de implantação do esquema. xml personalizado é alterado, mas o valor do caminho do atributo CustomSchema não é atualizado. Como resultado, a instância de lista não pode localizar o arquivo *Schema. xml* no caminho antigo que é especificado pelo atributo CustomSchema quando o recurso é ativado.

 Para resolver esse problema, atualize o caminho do local de implantação do arquivo *Schema. xml* no atributo CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Sessão de depuração do SharePoint encerrada pelo IIS
 Esse problema ocorre se você definir um ponto de interrupção em uma solução do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint, escolher a tecla **F5** para executá-lo e permanecer em um ponto de interrupção com mais de 90 segundos.

### <a name="error-message"></a>Mensagem de erro
 O processo do servidor Web que estava sendo depurado foi encerrado pelo Serviços de Informações da Internet (IIS). Você pode evitar esse problema definindo as configurações de ping do pool de aplicativos no IIS. Consulte a ajuda para obter mais detalhes.

### <a name="resolution"></a>Resolução
 Por padrão, o pool de aplicativos do IIS aguarda 90 segundos para que um aplicativo responda antes de fechar o aplicativo. Esse processo é conhecido como "executar ping" no aplicativo. Para resolver esse problema, você pode aumentar o tempo de espera ou desabilitar totalmente o ping do aplicativo.

##### <a name="to-access-the-iis-app-pool-settings"></a>Para acessar as configurações do pool de aplicativos do IIS

1. Abra o Gerenciador do IIS.

2. No painel **conexões** , expanda o nó servidor do SharePoint e escolha o nó **pools de aplicativos** .

3. Na página **pools de aplicativos** , escolha o pool de aplicativos do SharePoint (normalmente "SharePoint-80") e, no painel **ações** , escolha o link **Configurações avançadas** .

4. Para aumentar o tempo de espera antes do tempo limite do IIS, altere o valor do **tempo de resposta máximo de ping (segundos)** para um valor maior que 90 segundos.

5. Para desabilitar o ping do IIS, defina **ping habilitado** como **falso**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>A retração automática deixa a instância de lista órfã no SharePoint
 Esse problema ocorre se você executar as etapas a seguir.

1. Crie uma definição de lista que tenha uma instância de lista no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Escolha a tecla **F5** para executar a solução.

3. Interrompa a depuração ou feche o site do SharePoint.

4. Abra novamente o site do SharePoint e abra a instância de lista.

### <a name="error-message"></a>Mensagem de erro
 Erro de servidor no aplicativo '/'.

### <a name="resolution"></a>Resolução
 Isso acontece porque depois de fechar uma sessão de depuração de uma solução do SharePoint, o recurso de cancelamento automático cancela a solução. O cancelamento exclui a definição de lista do SharePoint, mas não exclui a instância da lista. A definição de lista subjacente é exigida pela instância de lista.

 Para resolver esse problema, implante a solução pelo, na barra de menus, escolhendo **compilar** > **implantar**. (Não depure a solução escolhendo a tecla **F5** .) Em seguida, exclua a instância de lista no SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>A solução do SharePoint original é substituída por uma versão exportada
 Se você exportar uma solução do SharePoint, importar a solução para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e, em seguida, implantar a solução de volta no mesmo site do qual ela foi exportada, a solução do SharePoint original será substituída. Esse problema não ocorrerá se você implantar a solução em um servidor que não tenha a solução original ativada.

### <a name="error-message"></a>Mensagem de erro
 nenhuma.

### <a name="resolution"></a>Resolução
 Para evitar a substituição de uma solução no site do qual ela foi exportada, altere os GUIDs da SolutionId e as IDs de recurso de todos os recursos importados no projeto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="error-appears-when-debugging-starts"></a>O erro aparece quando a depuração é iniciada
 Quando você começa a depurar uma solução do SharePoint no Visual Studio, um erro indica que o Visual Studio não pôde carregar o arquivo Web. config porque a chave fornecida não estava no dicionário.

### <a name="error-message"></a>Mensagem de erro
 Não foi possível carregar o arquivo de configuração Web. config. Verifique o arquivo em busca de qualquer elemento XML malformado e tente novamente. Ocorreu o seguinte erro: a chave fornecida não estava presente no dicionário.

### <a name="resolution"></a>Resolução
 Para resolver esse problema, verifique se o valor da propriedade URL do site do projeto do SharePoint no Visual Studio corresponde à URL atribuída à zona padrão para os mapeamentos de acesso alternativos do aplicativo Web. Você não pode resolver o erro usando outra zona, como intranet, para a URL. A URL do site para o projeto e a URL na zona padrão devem corresponder. Para acessar mapeamentos alternativos de acesso, abra o utilitário administração central do SharePoint 2010, escolha o link **Gerenciamento de aplicativos** e, em **aplicativos Web**, escolha o link **configurar mapeamentos alternativos de acesso** . Para obter mais informações, consulte [criar zonas para aplicativos Web](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Consulte também

- [Solução de problemas de empacotamento e implantação do SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Compilar e depurar soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)