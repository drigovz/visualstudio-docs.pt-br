---
title: Implantar, publicar, & atualizar pacotes de soluções SharePoint
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444964"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Implantar, publicar e atualizar pacotes de soluções SharePoint
  Depois de desenvolver uma solução SharePoint no Visual Studio, você pode implantar seu arquivo de pacote (.wsp) em um servidor SharePoint local ou publicá-lo em um servidor SharePoint remoto ou local. Se você implantar os arquivos, você pode personalizar como os arquivos do pacote (.wsp) são implantados.

> [!NOTE]
> Atualmente, apenas soluções sandboxpodem ser publicadas em servidores remotos do SharePoint. Para obter mais informações, consulte [considerações sobre a solução Sandboxed](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Implantar, publicar e atualizar
 *A implantação* refere-se à cópia de um arquivo de solução SharePoint construído a partir de um projeto SharePoint no Visual Studio para um host local. Em uma solução implantada, você pode configurar as etapas de implantação, como a reciclagem do pool de Serviços de Informação da Internet (IIS), ativando a solução após a implantação, e assim por diante. Para implantar, use o comando **Implantar** no menu **Construir.** Para obter mais informações, consulte [Como: Editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [como: implantar e publicar uma solução SharePoint em um site local do SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *A publicação* refere-se ao upload de um arquivo de solução SharePoint sandboxed para um site remoto do SharePoint; ou seja, um site localizado em outro sistema. Você também pode publicar um arquivo de solução sandboxed do SharePoint em um site local do SharePoint, mas, independentemente de o site publicado ser local ou remoto, você não pode configurar suas etapas de implantação.

 *A atualização* refere-se à atualização de uma solução SharePoint publicada remotamente ou localmente. Depois que qualquer alteração é feita na solução SharePoint no Visual Studio, você altera o nome do arquivo do pacote da solução, republica a solução e, em seguida, atualiza a solução depois que ela republica com sucesso. Se você republicar uma solução publicada localmente, poderá substituir o arquivo de solução existente.

## <a name="deploy-packages"></a>Implantar pacotes
 Você pode implantar arquivos de pacote para o servidor SharePoint em seu computador de desenvolvimento para testes e depuração. Você também pode criar um arquivo de pacote que você pode instalar em outro computador escolhendo o botão **Publicar para sistema de arquivos** na caixa de diálogo **Publicar.** O pacote é criado e copiado para o caminho de arquivo local especificado. Para implantar uma solução SharePoint no servidor local, use o comando **Implantar** no menu **Construir.** Para obter mais informações, consulte [Como implantar e publicar uma solução SharePoint em um site local do SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Para saber como implantar uma definição de lista, adicionar um receptor de eventos e usar o Designer de recursos e o designer de pacotes, consulte [Passo a Passo: Implante uma definição de lista de tarefas do projeto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Personalize o processo de implantação
 A tabela a seguir mostra as duas configurações de implantação que você pode usar quando você depura e implanta uma solução SharePoint.

|Configuração de implantação|Descrição|
|------------------------------|-----------------|
|Padrão|A configuração de implantação padrão. As seguintes etapas de implantação são executadas:<br /><br /> 1. Execute o comando de pré-implantação.<br />2. Recicle o pool de aplicativos IIS.<br />3. Retraia a solução.<br />4. Adicionar solução.<br />5. Ativar recursos.<br />6. Execute o comando pós-implantação.<br /><br /> Quando um pacote é desinstalado, as seguintes etapas de retração são executadas.<br /><br /> 1. Recicle o pool de aplicativos IIS.<br />2. Solução de retração.|
|Sem ativação|Essa configuração de implantação executa as mesmas etapas da configuração Padrão, mas ignora a etapa de ativação.|

 Você pode criar suas próprias configurações de implantação para concluir uma única etapa ou alterar a ordem das etapas no processo de implantação. Para obter mais informações, [consulte Como: Editar uma configuração de implantação do SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Você também pode adicionar comandos para executar antes e depois da implantação. Para obter mais informações, [consulte Como: Definir comandos de implantação do SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publicar pacotes para um servidor remoto ou local
 Para publicar uma solução SharePoint sandboxed em um servidor remoto, na barra de menus, escolha **Construir**, **Publicar**e, em seguida, na caixa `https://someremoteserver.sharepoint.microsoftonline.com`de diálogo **Publicar,** escolha o botão Publicar para compartilhar **site,** fornecendo a URL do servidor remoto, como .

 Para publicar uma solução SharePoint em um servidor local, na caixa de diálogo **Publicar,** escolha o botão **Publicar para o sistema de arquivos,** fornecendo um caminho local do sistema.

 Depois que uma solução é publicada com sucesso no SharePoint, a solução aparece na **Galeria de Soluções** onde você pode ativá-la. Para obter mais informações, consulte [Como implantar, publicar e atualizar as soluções SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Atualizar pacotes publicados
 Se você fizer qualquer alteração em um projeto do SharePoint no Visual Studio após sua publicação, o pacote publicado deve ser atualizado para incluir as alterações. Para atualizar com sucesso, um pacote deve ter um nome único. Se um pacote com o mesmo nome for encontrado no site do SharePoint - o que pode ocorrer quando você está atualizando um aplicativo existente - um erro o alerta para o conflito de nome do arquivo e permite que você renomeie o pacote. Após ser republicado, o novo pacote aparece no site do SharePoint e pode ser atualizado. Um pacote atualizado atualiza a solução usando dados do pacote mais antigo e, em seguida, ativa a solução no SharePoint. Para obter mais informações, consulte [Como implantar, publicar e atualizar as soluções SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Confira também
- [Pacote e implante soluções SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
