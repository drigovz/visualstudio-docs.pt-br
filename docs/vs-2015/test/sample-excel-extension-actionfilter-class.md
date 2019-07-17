---
title: 'Extensão do Excel de exemplo: Classe ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c1dda46ed0e62649a576a12c9f9e48561ec891
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158173"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensão do Excel de exemplo: Classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa classe interna estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e representa um filtro para as ações do teste em um elemento [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
## <a name="simple-properties"></a>Propriedades Simples  
 Essas propriedades somente leitura permitem ao desenvolvedor especificar como esse filtro de ação de teste deve ser executado pelo framework de teste de IU codificado. Por exemplo, a propriedade <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornece o nome do filtro de ação. Outras propriedades obtém a <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> do filtro de ação, o <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, o nome do <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> das ações de teste que são filtradas por esse filtro de ação de teste. Outras indicam se deseja <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e também se a ação de teste é <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>Método ProcessRule  
 Esse método é chamado pela estrutura de teste de IU codificado e executa o filtro em relação à <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> fornecida. Essa substituição específica remove uma ação de escolha do mouse em uma célula quando a próxima ação na pilha enviar pressionamentos de teclas para a célula. Em seguida, ele retorna `false`.  
  
## <a name="private-methods"></a>Métodos privados  
 O método `IsLeftClick` determina se a ação fornecida representa um clique com o botão esquerdo do mouse. O método `AreActionsOnSameExcelCell` determina se duas fornecidas ações são executadas na mesma célula do Excel.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
