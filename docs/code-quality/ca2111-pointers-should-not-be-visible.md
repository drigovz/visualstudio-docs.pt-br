---
title: 'CA2111: Ponteiros não devem ser visíveis'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a93f776ac6e133b0ebf79d1dfa56f802ff66e5f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232778"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Ponteiros não devem ser visíveis

|||
|-|-|
|NomeDoTipo|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um <xref:System.UIntPtr?displayProperty=fullName> campo público ou <xref:System.IntPtr?displayProperty=fullName> protegido não é somente leitura.

## <a name="rule-description"></a>Descrição da regra
 <xref:System.IntPtr>e <xref:System.UIntPtr> são tipos de ponteiro que são usados para acessar memória não gerenciada. Se um ponteiro não for privado, interno ou somente leitura, o código mal-intencionado poderá alterar o valor do ponteiro, potencialmente permitindo o acesso a locais arbitrários na memória ou causando falhas de aplicativo ou sistema.

Se você pretende proteger o acesso ao tipo que contém o campo de ponteiro, consulte [CA2112: Os tipos protegidos não devem expor](../code-quality/ca2112-secured-types-should-not-expose-fields.md)campos.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Proteja o ponteiro tornando-o somente leitura, interno ou privado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir um aviso dessa regra se você não depender do valor do ponteiro.

## <a name="example"></a>Exemplo
O código a seguir mostra os ponteiros que violam e satisfazem a regra. Observe que os ponteiros não privados também violam a regra [CA1051: Não declare campos](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)de instância visíveis.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2112: Tipos protegidos não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051: Não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Consulte também

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>