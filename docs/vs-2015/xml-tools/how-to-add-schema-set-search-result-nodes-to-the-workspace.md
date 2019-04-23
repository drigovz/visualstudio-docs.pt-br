---
title: 'Como: Adicionar nós de resultados de pesquisa de conjunto de esquema para o espaço de trabalho | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5df4b9c3bdefb6b807850e2b9f58fed8b2fd2a3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670102"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Como: Adicionar nós de resultados da pesquisa de esquema ao workspace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico explica como adicionar os nós que são realçadas em XML Schema Explorer como resultado de uma pesquisa de palavra-chave no workspace.  
  
> [!NOTE]
>  Somente os nós globais podem ser adicionados para o [espaço de trabalho](../xml-tools/xml-schema-designer-workspace.md).  
  
 Este exemplo usa a amostra [esquema de ordem de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Para adicionar nós definidos do resultado de esquema  
  
1.  Siga as etapas em [como: Criar e editar um arquivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Tipo "purchaseOrder" na caixa de texto de pesquisa do [XML Explorer](../xml-tools/xml-schema-explorer.md) ferramentas e clique no botão de pesquisa.  
  
     ![Pesquisa de palavra-chave do XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Os resultados de pesquisa são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical.  
  
3.  Adicionar os resultados da pesquisa para o espaço de trabalho clicando o **adicionar nós realçados ao espaço de trabalho** botão no painel de resultados de resumo.  
  
     ![Resultado da pesquisa do XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     O `purchaseOrder` nó e o `PurchaseOrderType` nó aparecem próximos uns dos outros na superfície de design da [modo de exibição gráfico](../xml-tools/graph-view.md). Porque os dois nós são relacionados (o elemento de `purchaseOrder` é do tipo de `PurchaseOrderType` ), uma seta é desenhada entre eles.
