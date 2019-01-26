---
title: 'CA2200: Relançar para preservar detalhes da pilha'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6f2dcc8a39e5ad29c590c5f0a7283154bfe1361a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036388"
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