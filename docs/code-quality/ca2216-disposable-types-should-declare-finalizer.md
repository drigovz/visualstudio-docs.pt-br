---
title: 'CA2216: Tipos descartáveis devem declarar o finalizador'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ac52bdb17aeb7d04e434d2b02ff9a905eab49a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305921"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Tipos descartáveis devem declarar o finalizador

|||
|-|-|
|NomeDoTipo|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> e tem campos que sugerem o uso de recursos não gerenciados, não implementa um finalizador, conforme descrito por <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da regra

Uma violação dessa regra será relatada se o tipo descartável contiver campos dos seguintes tipos:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, implemente um finalizador que chama o método <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra se o tipo não implementar <xref:System.IDisposable> com a finalidade de liberar recursos não gerenciados.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo que viola essa regra.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Regras relacionadas

[CA2115: Chame GC. KeepAlive ao usar recursos nativos @ no__t-0

[CA1816: Chame GC. SuppressFinalize corretamente @ no__t-0

[CA1049: Tipos que possuem recursos nativos devem ser descartáveis @ no__t-0

## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)