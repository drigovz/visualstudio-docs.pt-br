---
title: 'Como: Adicionar ou remover conexões do SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c094ad703727903e7109d6a748b8383e4cad7d6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435478"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Como: Adicionar ou remover conexões do SharePoint
  Gerenciador de servidores permite que você procure sites do SharePoint, bem como conexões de dados. No entanto, antes de você pode procurar o conteúdo de um site do SharePoint você deve adicioná-lo para o **conexões do SharePoint** nó.

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Para adicionar um site do SharePoint para o nó de conexões do SharePoint

1. Na barra de menus, escolha **modo de exibição**, **Gerenciador de servidores**.

2. Na **Gerenciador de servidores**, escolha o **conexões do SharePoint** nó e em seguida, na barra de menus, escolha **ferramentas** > **adicionar o SharePoint Conexão**.

3. No **Adicionar Conexão do SharePoint** , digite o [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] do site do SharePoint (por exemplo, http://testserver/sites/unittests).

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Para excluir um site do SharePoint a partir do nó de conexões do SharePoint

1. Na barra de menus, escolha **modo de exibição**, **Gerenciador de servidores** para abrir **Gerenciador de servidores**.

2. Expanda o **conexões do SharePoint** nó para revelar o site do SharePoint que você deseja excluir da **Gerenciador de servidores**.

3. Escolha o site e, em seguida, na barra de menus, escolha **edite** > **excluir**.

    > [!NOTE]
    > Essa etapa não exclui o site subjacente; Ele exclui apenas a conexão do **Gerenciador de servidores**.

## <a name="see-also"></a>Consulte também
- [Procurar conexões do SharePoint usando o Gerenciador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
