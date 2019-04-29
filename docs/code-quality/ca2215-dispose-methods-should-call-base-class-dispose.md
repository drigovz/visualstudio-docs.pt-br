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
ms.openlocfilehash: 203fc14097e0c6d2fbdaee1689deffdfe814eb63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541891"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Métodos Dispose devem chamar o descarte da classe base

|||
|-|-|
|NomeDoTipo|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> herda de um tipo que também implementa <xref:System.IDisposable>. O <xref:System.IDisposable.Dispose%2A> método do tipo de herança não chama o <xref:System.IDisposable.Dispose%2A> método do tipo pai.

## <a name="rule-description"></a>Descrição da regra
 Se um tipo herda de um tipo descartável, ele deve chamar o <xref:System.IDisposable.Dispose%2A> método do tipo base de dentro de seu próprio <xref:System.IDisposable.Dispose%2A> método. Chamar o método de tipo base Dispose garante que todos os recursos criados pelo tipo de base são liberados.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, chame `base`.<xref:System.IDisposable.Dispose%2A> no seu <xref:System.IDisposable.Dispose%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 É seguro suprimir um aviso nessa regra, se a chamada para `base`.<xref:System.IDisposable.Dispose%2A> ocorre em um nível mais profundo de chamada que as verificações de regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeA` que implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `TypeB` que herda do tipo `TypeA` e chama corretamente sua <xref:System.IDisposable.Dispose%2A> método.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable?displayProperty=fullName>
- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)