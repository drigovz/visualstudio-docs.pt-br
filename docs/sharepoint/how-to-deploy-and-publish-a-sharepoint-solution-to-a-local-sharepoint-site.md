---
title: Implantar a solução do SharePoint & publicar no site local do SharePoint
titleSuffix: ''
description: Examine como implantar ou publicar soluções do SharePoint em um servidor do SharePoint local em seu computador de desenvolvimento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 65683544f345a2378fdec559f582985ffec7bc43
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903579"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Como implantar e publicar uma solução do SharePoint em um site do SharePoint local
  Você pode implantar ou publicar soluções do SharePoint em um servidor do SharePoint local em seu computador de desenvolvimento. O processo de implantação copia o arquivo *. wsp* para o servidor do SharePoint, instala a solução e ativa os recursos. O processo de publicação só copia o arquivo *. wsp* para o servidor do SharePoint e o instala. Você deve ativá-lo manualmente para habilitá-lo no SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Para implantar uma solução do SharePoint no servidor do SharePoint local

1. Em **Gerenciador de soluções**, escolha o projeto que você deseja implantar.

2. Na barra de menus, escolha **Compilar**, **implantar solução**.

     O arquivo *. wsp* é criado e instalado no servidor do SharePoint local. Além disso, os recursos são ativados.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Para publicar uma solução do SharePoint em um servidor do SharePoint local

1. No **Gerenciador de soluções**, abra o menu de atalho do projeto do SharePoint que você deseja publicar e escolha **publicar**.

2. Na caixa de diálogo **publicar** , escolha o botão de opção **publicar no sistema de arquivos** .

3. Na caixa de texto **local de destino** , insira um caminho local e, em seguida, escolha o botão **publicar** .

     O progresso da publicação aparece na janela **saída** do Visual Studio. Quando o processo é concluído, o arquivo da solução (*. wsp*) é instalado no servidor do SharePoint local. No entanto, ele ainda deve ser ativado para ser usado no SharePoint. Se o arquivo de solução já existir, ocorrerá um erro e perguntará se você deseja substituir o arquivo existente. Para obter informações sobre como atualizar o pacote, consulte a seção sobre como atualizar pacotes remotos em [como implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Confira também
- [Como implantar, publicar e atualizar soluções do SharePoint em um servidor remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Criar pacotes de solução do SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Como: personalizar um pacote de solução do SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Como adicionar e remover recursos e itens para um pacote usando o designer de pacotes](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
