---
title: Extensões de depuração para as ferramentas do SharePoint no Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e170a5ed703a9bf5aae2e73126de52ecf88e8084
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785342"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Extensões de depuração para as ferramentas do SharePoint no Visual Studio
  Você pode depurar extensões de ferramentas do SharePoint na instância experimental ou na instância regular do Visual Studio. Se você precisar solucionar problemas de comportamento de uma extensão, também poderá modificar valores de registro para exibir informações de erro adicionais e configurar como o Visual Studio executa comandos do SharePoint.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Depurar extensões na instância experimental do Visual Studio
 Para proteger seu ambiente de desenvolvimento do Visual Studio contra a corrupção acidental por extensões não testadas, o SDK do Visual Studio fornece uma instância alternativa do Visual Studio, chamada de *instância experimental*, que você pode usar para instalar e testar extensões. Você desenvolve novas extensões usando a instância regular do Visual Studio, mas você as depura e executa na instância experimental. Para obter mais informações, consulte [a instância experimental](../extensibility/the-experimental-instance.md).

 Se você usar um projeto VSIX para implantar sua extensão e o projeto VSIX for o projeto de inicialização em sua solução, o Visual Studio instalará e executará automaticamente a extensão na instância experimental quando você depurar sua solução. O projeto de inicialização é o projeto que é iniciado quando você depura uma solução que contém vários projetos. Para obter mais informações sobre como usar um projeto VSIX para implantar sua extensão, consulte [implantar extensões para as ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Para obter exemplos que demonstram como depurar vários tipos de extensões na instância experimental do Visual Studio, consulte as instruções a seguir:

- [Walkthrough: estender um tipo de item de projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Walkthrough: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Walkthrough: estender Gerenciador de Servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Walkthrough: chamar o modelo de objeto de cliente do SharePoint em uma extensão Gerenciador de Servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Depurar extensões na instância regular do Visual Studio
 Se você quiser depurar seu projeto de extensão na instância regular do Visual Studio, primeiro instale a extensão na instância regular. Em seguida, anexe o depurador a um segundo processo do Visual Studio. Depois de concluir, você poderá remover a extensão para que ela não seja mais carregada no computador de desenvolvimento.

#### <a name="to-install-the-extension"></a>Para instalar a extensão

1. Feche todas as instâncias do Visual Studio.

2. Na pasta de saída da compilação para o projeto de extensão, abra o arquivo *. vsix* clicando duas vezes nele ou abrindo o menu de atalho e escolhendo **abrir**:

3. Na caixa de diálogo **instalador de extensão do Visual Studio** , escolha a edição do Visual Studio na qual você deseja instalar a extensão e, em seguida, escolha o botão **instalar** .

     O Visual Studio instala os arquivos de extensão em nome de extensão de \\ *nome de autor*%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions \\ *extension name* \\ *versão*. As três últimas pastas neste caminho são construídas nos `Author` elementos, `Name` e `Version` no arquivo *extension. vsixmanifest* para a extensão.

4. Depois que o Visual Studio instalar a extensão, escolha o botão **fechar** .

#### <a name="to-debug-the-extension"></a>Para depurar a extensão

1. Abra o Visual Studio com privilégios de administrador e abra o projeto de extensão. As etapas a seguir se referem a essa instância do Visual Studio como a *primeira instância*.

2. Inicie outra instância do Visual Studio com privilégios de administrador. As etapas a seguir referem-se a essa instância do Visual Studio como a *segunda instância*.

3. Alterne para a primeira instância do Visual Studio.

4. Na barra de menus, escolha **depurar**, **anexar ao processo**.

5. Na lista **processos disponíveis** , escolha *devenv.exe*. Essa entrada se refere à segunda instância do Visual Studio; Esta é a instância na qual você deseja depurar a extensão do projeto.

6. Escolha o botão **anexar** .

     O Visual Studio executa o projeto de extensão no modo de depuração.

7. Alterne para a segunda instância do Visual Studio.

8. Crie um novo projeto do SharePoint que carregue sua extensão. Por exemplo, se você estiver Depurando uma extensão para itens de projeto de definição de lista, crie um projeto de **definição de lista** .

9. Execute todas as etapas necessárias para testar o código de extensão.

10. Quando terminar de depurar a extensão, feche a segunda instância do Visual Studio.

#### <a name="to-remove-the-extension"></a>Para remover a extensão

1. No Visual Studio, na barra de menus, escolha **ferramentas**, **extensões e atualizações**.

     A caixa de diálogo **Extensões e Atualizações** é aberta.

2. Na lista de extensões, escolha o nome da extensão e, em seguida, escolha o botão **desinstalar** .

3. Na caixa de diálogo exibida, escolha o botão **Sim** para confirmar que você deseja desinstalar a extensão.

4. Escolha o botão **reiniciar agora** para concluir a desinstalação.

## <a name="debug-sharepoint-commands"></a>Depurar comandos do SharePoint
 Se desejar depurar um comando do SharePoint que faça parte de uma extensão de ferramentas do SharePoint, você deverá anexar o depurador ao processo de *vssphost4.exe* . Esse é o processo de host de 64 bits que executa comandos do SharePoint. Para obter mais informações sobre os comandos e *vssphost4.exe*do SharePoint, consulte [chamar os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Para anexar o depurador ao processo de vssphost4.exe

1. Comece a depurar sua extensão na instância experimental do Visual Studio ou na instância regular do Visual Studio seguindo as instruções acima.

2. Na instância do Visual Studio na qual você está executando o depurador, na barra de menus, escolha **depurar**, **anexar ao processo**.

3. Na lista **processos disponíveis** , escolha *vssphost.exe*.

    > [!NOTE]
    > Se vssphost.exe não aparecer na lista, você deverá iniciar o processo de *vssphost4.exe* na instância do Visual Studio na qual você está executando a extensão. Normalmente, você faz isso executando uma ação que faz com que o Visual Studio se conecte ao site do SharePoint no computador de desenvolvimento. Por exemplo, o Visual Studio inicia *vssphost4.exe* quando você expande um nó de conexão do site (um nó que EXIBE uma URL do site) no nó **conexões do sharepoint** na janela **Gerenciador de servidores** ou quando você adiciona determinados itens de projeto do SharePoint, como a **instância da lista** ou itens do receptor de **eventos** , a um projeto do SharePoint.

4. Escolha o botão **anexar** .

5. Na instância do Visual Studio que está sendo depurada, execute as etapas necessárias para executar o comando.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Modificar valores do registro para ajudar a depurar extensões de ferramentas do SharePoint
 Ao depurar uma extensão das ferramentas do SharePoint no Visual Studio, você pode modificar valores no registro para ajudá-lo a solucionar problemas da extensão. Os valores existem na chave **HKEY_CURRENT_USER \software\microsoft\visualstudio\11.0\SharePointTools** . Esses valores não existem por padrão.

 Para ajudar a solucionar qualquer extensão das ferramentas do SharePoint, você pode criar e definir o valor EnableDiagnostics. A tabela a seguir descreve esse valor.

|Valor|Descrição|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD que especifica se as mensagens de diagnóstico são exibidas na janela de **saída** .<br /><br /> Para exibir mensagens de diagnóstico, defina esse valor como 1. Para parar de exibir mensagens, defina esse valor como 0 ou exclua esse valor.<br /><br /> Para gravar mensagens na janela de **saída** de uma extensão de ferramentas do SharePoint, use o serviço de projeto do SharePoint. Para obter mais informações, consulte [usar o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Se sua extensão incluir um comando do SharePoint, você poderá criar e definir valores adicionais para ajudar a solucionar o comando. A tabela a seguir descreve esses valores.

|Valor|Descrição|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD que especifica se uma caixa de diálogo deve ser exibida, permitindo que você anexe o depurador a *vssphost4.exe* assim que ele for iniciado. Isso é útil se o comando que você deseja depurar é executado por vssphost.exe imediatamente após o início e não há tempo suficiente para anexar manualmente o depurador antes de o comando ser executado. Para exibir a caixa de diálogo, *vssphost4.exe* chama o <xref:System.Diagnostics.Debugger.Break%2A> método quando ele é iniciado.<br /><br /> Para habilitar esse comportamento, defina esse valor como 1. Para desativar esse comportamento, defina esse valor como 0 ou exclua esse valor.<br /><br /> Se você definir esse valor como 1, talvez também queira aumentar o valor de HostProcessStartupTimeout para dar a si mesmo tempo suficiente para anexar o depurador antes que o Visual Studio Espere *vssphost4.exe* sinalizar que ele foi iniciado com êxito.|
|ChannelOperationTimeout|REG_DWORD que especifica o tempo, em segundos, que o Visual Studio aguarda até que um comando do SharePoint seja executado. Se o comando não for executado no tempo, um <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> será lançado.<br /><br /> O padrão é 120 segundos.|
|HostProcessStartupTimeout|REG_DWORD que especifica o tempo, em segundos, que o Visual Studio aguarda *vssphost4.exe* para sinalizar que ele foi iniciado com êxito. Se *vssphost4.exe* não sinalizar um início bem-sucedido no tempo, um <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> será lançado.<br /><br /> O padrão é 60 segundos.|
|MaxReceivedMessageSize|REG_DWORD que especifica o tamanho máximo permitido, em bytes, das mensagens do WCF que são passadas entre o Visual Studio e *vssphost4.exe*.<br /><br /> O padrão é 1.048.576 bytes (1 MB).|
|MaxStringContentLength|REG_DWORD que especifica o tamanho máximo permitido, em bytes, de cadeias de caracteres que são transmitidas entre o Visual Studio e *vssphost4.exe*.<br /><br /> O padrão é 1.048.576 bytes (1 MB).|

## <a name="see-also"></a>Confira também

- [Estenda as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Implantar extensões para as ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
