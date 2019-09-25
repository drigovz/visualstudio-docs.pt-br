---
title: 'CA1064: Exceções devem ser públicas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffc12d8d047be1bb13fcac133a61b047152ce3d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235325"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Exceções devem ser públicas

|||
|-|-|
|NomeDoTipo|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Uma exceção não pública deriva diretamente de <xref:System.Exception>, <xref:System.SystemException>ou <xref:System.ApplicationException>.

## <a name="rule-description"></a>Descrição da regra
Uma exceção interna só é visível dentro de seu próprio escopo interno. Depois que a exceção falha fora do escopo interno, somente a exceção de base pode ser usada para capturar a exceção. Se a exceção interna for herdada de <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>, o código externo não terá informações suficientes para saber o que fazer com a exceção.

Mas, se o código tiver uma exceção pública que, posteriormente, é usada como base para uma exceção interna, é razoável assumir que o código ainda será capaz de fazer algo inteligente com a exceção base. A exceção pública terá mais informações do que o fornecido pelo <xref:System.Exception>, <xref:System.SystemException>ou <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Torne a exceção pública ou derive a exceção interna de uma exceção pública que não <xref:System.Exception>seja, <xref:System.SystemException>ou. <xref:System.ApplicationException>

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir uma mensagem dessa regra se você tiver certeza de que, em todos os casos, a exceção particular será detectada em seu próprio escopo interno.

## <a name="example"></a>Exemplo
Essa regra é acionada no primeiro método de exemplo, FirstCustomException porque a classe de exceção deriva diretamente da exceção e é interna. A regra não é acionada na classe SecondCustomException porque, embora a classe também derive diretamente da exceção, a classe é declarada pública. A terceira classe também não aciona a regra porque ela não deriva diretamente de <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>ou <xref:System.ApplicationException?displayProperty=fullName>.

[!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
