---
title: 'CA2220: Os finalizadores devem chamar o finalizador de classe base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 034f80c9198ab098070e6642f4a4d96cff1744c5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927640"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Os finalizadores devem chamar o finalizador de classe base

|||
|-|-|
|NomeDoTipo|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um tipo que substitui <xref:System.Object.Finalize%2A?displayProperty=fullName> não chama o <xref:System.Object.Finalize%2A> método na sua classe base.

## <a name="rule-description"></a>Descrição da regra

A finalização deve ser propagada em toda a hierarquia de herança. Para garantir isso, os tipos devem chamar sua classe base <xref:System.Object.Finalize%2A> método de dentro de seus próprios <xref:System.Object.Finalize%2A> método. O compilador C# adiciona a chamada para o finalizador da classe base automaticamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, chame o tipo base <xref:System.Object.Finalize%2A> método de sua <xref:System.Object.Finalize%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Alguns compiladores que direcionam o common language runtime inserir uma chamada para o finalizador do tipo base em Microsoft intermediate language (MSIL). Se um aviso nessa regra for relatado, o compilador não insere a chamada e você deve adicioná-lo ao seu código.

## <a name="example"></a>Exemplo

O exemplo de Visual Basic a seguir mostra um tipo `TypeB` que chama corretamente o <xref:System.Object.Finalize%2A> método na sua classe base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Consulte também

- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)