---
title: 'CA2215: Métodos Dispose devem chamar o descarte da classe base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f3c118b097dbcd9eba8a5755672bde9c11cb13a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920304"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Métodos Dispose devem chamar o descarte da classe base

|||
|-|-|
|NomeDoTipo|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> herda de um tipo que também implementa <xref:System.IDisposable>. O <xref:System.IDisposable.Dispose%2A> método do tipo de herança não chama o <xref:System.IDisposable.Dispose%2A> método do tipo pai.

## <a name="rule-description"></a>Descrição da regra
Se um tipo for herdado de um tipo descartável, ele <xref:System.IDisposable.Dispose%2A> deverá chamar o método do tipo base de dentro <xref:System.IDisposable.Dispose%2A> de seu próprio método. Chamar o método de tipo base Dispose garante que todos os recursos criados pelo tipo base sejam liberados.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, chame `base`.<xref:System.IDisposable.Dispose%2A> em seu <xref:System.IDisposable.Dispose%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se a chamada para `base`.<xref:System.IDisposable.Dispose%2A> ocorre em um nível de chamada mais profundo do que as verificações de regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um `TypeA` tipo que <xref:System.IDisposable>implementa.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um `TypeB` tipo que herda de `TypeA` tipo e chama corretamente <xref:System.IDisposable.Dispose%2A> seu método.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable?displayProperty=fullName>
- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)