---
title: 'Extensão de amostra do Excel: classe ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672178"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensão de exemplo do Excel: classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa classe interna estende a classe [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) e representa um filtro para ações de teste em um elemento [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

## <a name="simple-properties"></a>Propriedades Simples
 Essas propriedades somente leitura permitem ao desenvolvedor especificar como esse filtro de ação de teste deve ser executado pelo framework de teste de IU codificado. Por exemplo, a propriedade `UITestActionFilter.Name` fornece o nome do filtro de ação. Outras propriedades obtém a `UITestActionFilter.Category` do filtro de ação, o `UITestActionFilter.FilterType`, o nome do `UITestActionFilter.Group` das ações de teste que são filtradas por esse filtro de ação de teste. Outras indicam se deseja `UITestActionFilter.ApplyTimeout` e também se a ação de teste é `UITestActionFilter.Enabled`.

## <a name="processrule-method"></a>Método ProcessRule
 Esse método é chamado pela estrutura de teste de IU codificado e executa o filtro em relação à `IUITestActionStack` fornecida. Essa substituição específica remove uma ação de escolha do mouse em uma célula quando a próxima ação na pilha enviar pressionamentos de teclas para a célula. Em seguida, ele retorna `false`.

## <a name="private-methods"></a>Métodos privados
 O método `IsLeftClick` determina se a ação fornecida representa um clique com o botão esquerdo do mouse. O método `AreActionsOnSameExcelCell` determina se duas fornecidas ações são executadas na mesma célula do Excel.

## <a name="see-also"></a>Consulte também

- [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
