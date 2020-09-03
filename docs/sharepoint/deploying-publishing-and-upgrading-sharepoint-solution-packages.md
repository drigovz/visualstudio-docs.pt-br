---
title: Implantar, publicar, & atualizar pacotes de solução do SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444964"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Implantar, publicar e atualizar pacotes de solução do SharePoint
  Depois de desenvolver uma solução do SharePoint no Visual Studio, você pode implantar seu arquivo de pacote (. wsp) em um servidor do SharePoint local ou publicá-lo em um servidor do SharePoint remoto ou local. Se você implantar os arquivos, poderá personalizar como os arquivos de pacote (. wsp) são implantados.

> [!NOTE]
> Atualmente, somente soluções em área restrita podem ser publicadas em servidores remotos do SharePoint. Para obter mais informações, consulte [Considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Implantar, publicar e atualizar
 A *implantação* refere-se à cópia de um arquivo de solução do SharePoint criado a partir de um projeto do SharePoint no Visual Studio para um host local. Em uma solução implantada, você pode configurar as etapas de implantação, como reciclar o pool de Serviços de Informações da Internet (IIS), ativar a solução após a implantação e assim por diante. Para implantar, use o comando **implantar** no menu **Compilar** . Para obter mais informações, consulte [como: editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [como implantar e publicar uma solução do SharePoint em um site do SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 A *publicação* refere-se ao carregamento de um arquivo de solução do SharePoint em área restrita para um site remoto do SharePoint; ou seja, um site localizado em outro sistema. Você também pode publicar um arquivo de solução de área restrita do SharePoint em um site do SharePoint local, mas independentemente se o site publicado no é local ou remoto, você não pode configurar suas etapas de implantação.

 A *atualização* refere-se à atualização de uma solução do SharePoint existente ou publicada localmente. Depois que as alterações forem feitas na solução do SharePoint no Visual Studio, você alterará o nome do arquivo de pacote da solução, republicará a solução e, em seguida, atualizará a solução depois que ela for republicada com êxito. Se você republicar uma solução publicada localmente, poderá substituir o arquivo de solução existente.

## <a name="deploy-packages"></a>Implantar pacotes
 Você pode implantar arquivos de pacote no servidor do SharePoint em seu computador de desenvolvimento para teste e depuração. Você também pode criar um arquivo de pacote que pode ser instalado em outro computador escolhendo o botão de opção **publicar no sistema de arquivos** na caixa de diálogo **publicar** . O pacote é criado e copiado para o caminho de arquivo local especificado. Para implantar uma solução do SharePoint no servidor local, use o comando **implantar** no menu **Compilar** . Para obter mais informações, consulte [como implantar e publicar uma solução do SharePoint em um site do SharePoint local](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Para saber como implantar uma definição de lista, adicionar um receptor de evento e usar o designer de recursos e o designer de pacotes, consulte [passo a passos: implantar uma definição de lista de tarefas de projeto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Personalizar o processo de implantação
 A tabela a seguir mostra as duas configurações de implantação que você pode usar ao depurar e implantar uma solução do SharePoint.

|Configuração de implantação|Descrição|
|------------------------------|-----------------|
|Padrão|A configuração de implantação padrão. As seguintes etapas de implantação são executadas:<br /><br /> 1. Execute o comando pré-implantação.<br />2. reciclar o pool de aplicativos do IIS.<br />3. cancelar solução.<br />4. Adicionar solução.<br />5. Ative os recursos.<br />6. Execute o comando pós-implantação.<br /><br /> Quando um pacote é desinstalado, as etapas de retração a seguir são executadas.<br /><br /> 1. reciclar o pool de aplicativos do IIS.<br />2. retrair solução.|
|Sem ativação|Essa configuração de implantação executa as mesmas etapas da configuração padrão, mas ignora a etapa de ativação.|

 Você pode criar suas próprias configurações de implantação para concluir uma única etapa ou alterar a ordem das etapas no processo de implantação. Para obter mais informações, consulte [como: editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Você também pode adicionar comandos para executar antes e após a implantação. Para obter mais informações, consulte [como: definir comandos de implantação do SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publicar pacotes em um servidor remoto ou local
 Para publicar uma solução do SharePoint em área restrita em um servidor remoto, na barra de menus, escolha **criar**, **publicar**e, em seguida, na caixa de diálogo **publicar** , escolha o botão de opção **publicar no SharePoint site** , fornecendo a URL do servidor remoto, como `https://someremoteserver.sharepoint.microsoftonline.com` .

 Para publicar uma solução do SharePoint em um servidor local, na caixa de diálogo **publicar** , escolha o botão de opção **publicar no sistema de arquivos** , fornecendo um caminho do sistema local.

 Depois que uma solução é publicada com êxito no SharePoint, a solução é exibida na **Galeria de soluções** , na qual você pode ativá-la. Para obter mais informações, consulte [como implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Atualizar pacotes publicados
 Se você fizer alterações em um projeto do SharePoint no Visual Studio depois que ele for publicado, o pacote publicado deverá ser atualizado para incluir as alterações. Para atualizar com êxito, um pacote deve ter um nome exclusivo. Se um pacote com o mesmo nome for encontrado no site do SharePoint, o que pode ocorrer quando você estiver atualizando um aplicativo existente, um erro alertará você sobre o conflito de nome de arquivo e permitirá que você renomeie o pacote. Depois de ser republicado, o novo pacote aparece no site do SharePoint e pode ser atualizado. Um pacote atualizado atualiza a solução usando dados do pacote mais antigo e ativa a solução no SharePoint. Para obter mais informações, consulte [como implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Confira também
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
