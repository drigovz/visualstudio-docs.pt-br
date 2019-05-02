---
title: 'Como: Adicionar nós ao workspace do gerenciador de esquema XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f38760e6a04bd9e88fd4ff6e8c9d31f30ba27647
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783226"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Como: Adicionar nós ao workspace do XML Schema Explorer

Este tópico explica como adicionar nós a [espaço de trabalho do Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md) da **XML Schema Explorer**. Isso pode ser obtido arrastando e soltando-os nós do **XML Schema Explorer** em uma exibição do Designer XSD ou usando o **XML Schema Explorer** menu de contexto. Você também pode adicionar nós que são realçadas como resultado de uma pesquisa executada pela **XML Schema Explorer**. Para obter mais informações, confira [Como: Adicionar nós de resultados de pesquisa de conjunto de esquema para o espaço de trabalho](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Somente os nós globais podem ser adicionados para o [espaço de trabalho do Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Para adicionar nós através do menu de contexto XML Explorer

1. Siga as etapas em [como: Criar e editar um arquivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Clique com botão direito no `PurchaseOrderType` nó no Gerenciador de XSD. Selecione **Mostrar no modo de exibição gráfico**.

     O nó de `purchaseOrderType` aparece na superfície de design do modo de gráfico.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Para arrastar e soltar sobre um nó para uma visualização

1. Clique com botão direito no `PurchaseOrderType` nó no modo de gráfico. Selecione **Mostrar em XML Schema Explorer**.

     O nó é realçado na **XML Schema Explorer**.

2. Clique com botão direito no `PurchaseOrderType` nó o **XML Schema Explorer** e selecione **Mostrar todas as referências**.

     O nó de `purchaseOrder` é realçado.

3. Arraste o nó de `purchaseOrder` sobre para o modo de exibição gráfico.

     O nó de `purchaseOrder` e o nó de `PurchaseOrderType` aparecem próximos uns dos outros na superfície de design do modo de gráfico. Porque os dois nós são relacionados (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Para adicionar nós que usam o esquema Explorer pesquisam o recurso

1. Tipo "purchaseOrder" na caixa de texto de pesquisa do [XML Explorer](../xml-tools/xml-schema-explorer.md) ferramentas e clique no botão de pesquisa.

     ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     Os resultados da pesquisa são realçados na **XML Schema Explorer** e marcados por escalas na barra de rolagem vertical.

2. Adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.

     ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     O `purchaseOrder` nó e o `PurchaseOrderType` nó aparecem próximos uns dos outros na superfície de design da [modo de exibição gráfico](../xml-tools/graph-view.md). Porque os dois nós são relacionados (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.

## <a name="see-also"></a>Consulte também

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)