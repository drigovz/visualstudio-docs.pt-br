---
title: Adicionar nós de resultados Pesquisar do conjunto de esquema XML para o espaço de trabalho
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba709e90de580aacda2034eca319a419583dac0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783684"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Como: Adicionar nós de resultados da pesquisa de conjunto de esquema ao workspace

Este tópico explica como adicionar nós realçados na **XML Schema Explorer** como resultado de uma pesquisa de palavra-chave no espaço de trabalho.

> [!NOTE]
> Somente os nós globais podem ser adicionados para o [espaço de trabalho](../xml-tools/xml-schema-designer-workspace.md).

 Este exemplo usa a amostra [esquema de ordem de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Para adicionar nós definidos do resultado de esquema

1. Siga as etapas em [como: Criar e editar um arquivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Tipo "purchaseOrder" na caixa de texto de pesquisa do [XML Explorer](../xml-tools/xml-schema-explorer.md) ferramentas e clique no botão de pesquisa.

     ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     Os resultados da pesquisa são realçados na **XML Schema Explorer** e marcados por escalas na barra de rolagem vertical.

3. Adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.

     ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     O `purchaseOrder` nó e o `PurchaseOrderType` nó aparecem próximos uns dos outros na superfície de design da [modo de exibição gráfico](../xml-tools/graph-view.md). Porque os dois nós são relacionados (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.