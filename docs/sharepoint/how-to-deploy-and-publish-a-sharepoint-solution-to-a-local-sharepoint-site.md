---
title: 'Como: Implantar e publicar uma solução do SharePoint em um Site do SharePoint Local | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 9537b3eef0d5da445d9456b414c89bbaac08ae87
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067749"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Como: Implantar e publicar uma solução do SharePoint em um site do SharePoint local
  Você pode implantar ou publicar soluções do SharePoint em um servidor local do SharePoint no computador de desenvolvimento. As cópias do processo de implantação do *. wsp* arquivo para o servidor do SharePoint instala a solução e, em seguida, ativa os recursos. Somente cópias de processar a publicação a *. wsp* arquivo para o servidor do SharePoint e o instala. Você deve ativar manualmente para habilitá-lo no SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Para implantar uma solução do SharePoint para o servidor local do SharePoint

1. Na **Gerenciador de soluções**, escolha o projeto que você deseja implantar.

2. Na barra de menus, escolha **construir**, **implantar solução**.

     O *. wsp* arquivo é criado e instalado no servidor do SharePoint local. Além disso, os recursos são ativados.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Para publicar uma solução do SharePoint em um servidor local do SharePoint

1. Na **Gerenciador de soluções**, abra o menu de atalho para o projeto do SharePoint que você deseja publicar e, em seguida, escolha **publicar**.

2. No **Publish** diálogo caixa, escolha o **publicar no sistema de arquivos** botão de opção.

3. No **local de destino** caixa de texto, insira um caminho local e, em seguida, escolha o **publicar** botão.

     O andamento da publicação é exibido no Visual Studio **saída** janela. Quando o processo for concluído, a solução (*. wsp*) arquivo é instalado no servidor do SharePoint local. No entanto, ele ainda deve ser ativado para ser usada no SharePoint. Se o arquivo de solução já existir, um erro ocorre e pergunta se você deseja substituir o arquivo existente. Para obter informações sobre como atualizar o pacote, consulte a seção sobre como atualizar pacotes remotos em [como: Implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Consulte também
- [Como: Implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Criar pacotes de solução do SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Como: Personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Como: Adicionar e remover funcionalidades e itens de um pacote usando o Designer de pacote](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
