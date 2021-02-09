---
title: 'Como: Adicionar ou remover conexões do SharePoint | Microsoft Docs'
description: Adicione ou remova as conexões do SharePoint usando o nó conexões do SharePoint na janela Gerenciador de Servidores do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 57ff132274ba7f720a845078b0424fe235d9c31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923456"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Como: Adicionar ou remover conexões do SharePoint
  Gerenciador de Servidores permite que você procure sites do SharePoint, bem como conexões de dados. No entanto, antes de poder procurar o conteúdo de um site do SharePoint, você deve adicioná-lo ao nó **conexões do SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Para adicionar um site do SharePoint ao nó conexões do SharePoint

1. Na barra de menus, escolha **Exibir**, **Gerenciador de servidores**.

2. Em **Gerenciador de servidores**, escolha o nó **conexões do SharePoint** e, na barra de menus, escolha **ferramentas**  >  **Adicionar conexão do SharePoint**.

3. Na caixa **Adicionar conexão do SharePoint** , insira o [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para o site do SharePoint (por exemplo, http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Para excluir um site do SharePoint do nó conexões do SharePoint

1. Na barra de menus, escolha **Exibir**, **Gerenciador de Servidores** para abrir **Gerenciador de servidores**.

2. Expanda o nó **conexões do SharePoint** para revelar o site do SharePoint que você deseja excluir do **Gerenciador de servidores**.

3. Escolha o site e, na barra de menus, escolha **Editar**  >  **excluir**.

    > [!NOTE]
    > Esta etapa não exclui o site subjacente; Ele exclui somente a conexão de **Gerenciador de servidores**.

## <a name="see-also"></a>Confira também
- [Procurar conexões do SharePoint usando Gerenciador de Servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
