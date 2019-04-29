---
title: 'CA2200: Relançar para preservar detalhes da pilha'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 55c58f098616a5c3c2d6ad72f56e8eda51f689be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796839"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Relançar para preservar detalhes da pilha

|||
|-|-|
|NomeDoTipo|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Uma exceção será gerada novamente e a exceção é especificada explicitamente no `throw` instrução.

## <a name="rule-description"></a>Descrição da regra

Depois que uma exceção é lançada, a parte das informações de que ele executa é o rastreamento de pilha. O rastreamento de pilha é uma lista de hierarquia de chamada de método que começa com o método que lança a exceção e termina com o método que captura a exceção. Se uma exceção é relançada, especificando a exceção no `throw` instrução, o rastreamento de pilha é reiniciado no método atual e a lista de chamadas de método entre o método original que gerou a exceção e o método atual for perdida. Para manter as informações de rastreamento de pilha original com a exceção, use o `throw` instrução sem especificar a exceção.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, relançar a exceção sem especificar a exceção explicitamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um método `CatchAndRethrowExplicitly`, que viola a regra e um método, `CatchAndRethrowImplicitly`, que satisfaz a regra.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]