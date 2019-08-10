---
title: 'CA1401: P-Invokes não devem ser visíveis'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e26daf68e0031358605427b310bb7284d43baf1b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922141"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes não devem ser visíveis

|||
|-|-|
|NomeDoTipo|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um método público ou protegido em um tipo público tem o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo (também implementado `Declare` pela palavra-chave [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]em).

## <a name="rule-description"></a>Descrição da regra
Os métodos que são marcados com <xref:System.Runtime.InteropServices.DllImportAttribute> o atributo (ou métodos que são definidos usando a `Declare` palavra- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]chave em) usam os serviços de invocação de plataforma para acessar código não gerenciado. Esses métodos não devem ser expostos. Ao manter esses métodos privados ou internos, certifique-se de que sua biblioteca não pode ser usada para violar a segurança, permitindo que os chamadores acessem APIs não gerenciadas que não podiam chamar de outra forma.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o nível de acesso do método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir declara um método que viola essa regra.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]