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
ms.openlocfilehash: 2efdc339500786de87c35b4caeb3c85cef5191b7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864092"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Como: Implantar e publicar uma solução do SharePoint em um site do SharePoint local
  Você pode implantar ou publicar soluções do SharePoint em um servidor local do SharePoint no computador de desenvolvimento. As cópias do processo de implantação do *. wsp* arquivo para o servidor do SharePoint instala a solução e, em seguida, ativa os recursos. Somente cópias de processar a publicação a *. wsp* arquivo para o servidor do SharePoint e o instala. Você deve ativar manualmente para habilitá-lo no SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Para implantar uma solução do SharePoint para o servidor local do SharePoint  
  
1.  Na **Gerenciador de soluções**, escolha o projeto que você deseja implantar.  
  
2.  Na barra de menus, escolha **construir**, **implantar solução**.  
  
     O *. wsp* arquivo é criado e instalado no servidor do SharePoint local. Além disso, os recursos são ativados.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Para publicar uma solução do SharePoint em um servidor local do SharePoint  
  
1.  Na **Gerenciador de soluções**, abra o menu de atalho para o projeto do SharePoint que você deseja publicar e, em seguida, escolha **publicar**.  
  
2.  No **Publish** diálogo caixa, escolha o **publicar no sistema de arquivos** botão de opção.  
  
3.  No **local de destino** caixa de texto, insira um caminho local e, em seguida, escolha o **publicar** botão.  
  
     O andamento da publicação é exibido no Visual Studio **saída** janela. Quando o processo for concluído, a solução (*. wsp*) arquivo é instalado no servidor do SharePoint local. No entanto, ele ainda deve ser ativado para ser usada no SharePoint. Se o arquivo de solução já existir, um erro ocorre e pergunta se você deseja substituir o arquivo existente. Para obter informações sobre como atualizar o pacote, consulte a seção sobre como atualizar pacotes remotos em [como: Implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Consulte também
 [Como: Implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Criar pacotes de solução do SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Como: Personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Como: Adicionar e remover funcionalidades e itens de um pacote usando o Designer de pacote](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
