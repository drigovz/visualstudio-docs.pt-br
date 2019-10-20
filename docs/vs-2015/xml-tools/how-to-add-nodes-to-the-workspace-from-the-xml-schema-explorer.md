---
title: Como adicionar nós ao espaço de trabalho do XML Schema Explorer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c8fe9d5ba8c096a03de7a9df85945f4aeb4a0a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656337"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Como: Adicionar nós ao workspace XML Schema Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico explica como adicionar nós ao espaço de [trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md) do XML Schema Explorer. Isso pode ser obtido arrastando e soltando-os nós XML Schema Explorer em uma exibição do designer XSD, ou usando o menu de contexto do gerenciador de esquema XML. Você também pode adicionar os nós que são realçadas como resultado de uma pesquisa executada por XML Schema Explorer. Para obter mais informações, consulte [como adicionar nós de resultado de pesquisa de conjunto de esquema ao espaço de trabalho](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Somente nós globais podem ser adicionados ao [espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).

### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Para adicionar nós através do menu de contexto XML Explorer

1. Siga as etapas em [como criar e editar um arquivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Clique com o botão direito do mouse no nó de `PurchaseOrderType` em um XSD Explorer. Selecione **Mostrar no modo de exibição de gráfico**.

     O nó de `purchaseOrderType` aparece na superfície de design do modo de gráfico.

### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Para arrastar e soltar sobre um nó para uma visualização

1. Clique com o botão direito do mouse no nó de `PurchaseOrderType` no modo de gráfico. Selecione **Mostrar no Gerenciador de esquema XML**.

     O nó é realçado em XML Schema Explorer.

2. Clique com o botão direito do mouse no nó `PurchaseOrderType` no XML Schema Explorer e selecione **Mostrar todas as referências**.

     O nó de `purchaseOrder` é realçado.

3. Arraste o nó de `purchaseOrder` sobre para o modo de exibição gráfico.

     O nó de `purchaseOrder` e o nó de `PurchaseOrderType` aparecem próximos uns dos outros na superfície de design do modo de gráfico. Porque os dois nós realted (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.

### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Para adicionar nós que usam o esquema Explorer pesquisam o recurso

1. Digite "purchaseOrder" na caixa de texto Pesquisar da barra de ferramentas do [Gerenciador de XML](../xml-tools/xml-schema-explorer.md) e clique no botão Pesquisar.

     ![Pesquisa de palavra-chave do Gerenciador de esquema XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Os resultados de pesquisa são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical.

2. Adicione os resultados da pesquisa ao espaço de trabalho clicando no botão **adicionar nós realçados ao espaço de trabalho** no painel resultados do resumo.

     ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     O nó `purchaseOrder` e o nó `PurchaseOrderType` aparecem ao lado um do outro na superfície de design do [modo de exibição de gráfico](../xml-tools/graph-view.md). Porque os dois nós são relacionados (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.

## <a name="see-also"></a>Consulte também
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
