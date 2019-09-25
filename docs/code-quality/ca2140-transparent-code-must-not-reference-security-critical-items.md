---
title: 'CA2140: O código transparente não deve referenciar itens críticos de segurança'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4f02938aed7456762f1ef51da716b6b96bdf437
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232157"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: O código transparente não deve referenciar itens críticos de segurança

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um método transparente:

- manipula um tipo de exceção de segurança crítica de segurança

- tem um parâmetro que está marcado como um tipo de segurança crítica

- tem um parâmetro genérico com restrições críticas de segurança

- tem uma variável local de um tipo crítico de segurança

- faz referência a um tipo marcado como segurança crítica

- chama um método que é marcado como segurança crítica

- faz referência a um campo marcado como segurança crítica

- Retorna um tipo marcado como segurança crítica

## <a name="rule-description"></a>Descrição da regra

Um elemento de código que é marcado com <xref:System.Security.SecurityCriticalAttribute> o atributo é crítico para segurança. Um método transparente não pode usar um elemento crítico para segurança. Se um tipo transparente tentar usar um tipo crítico de segurança a <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , ou <xref:System.FieldAccessException> será gerado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, siga um destes procedimentos:

- Marcar o elemento de código que usa o código crítico de segurança <xref:System.Security.SecurityCriticalAttribute> com o atributo

     \- ou -

- Remova o <xref:System.Security.SecurityCriticalAttribute> atributo dos elementos de código marcados como segurança crítico e, em vez disso, marque- <xref:System.Security.SecuritySafeCriticalAttribute> os <xref:System.Security.SecurityTransparentAttribute> com o atributo ou.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo

Nos exemplos a seguir, um método transparente tenta fazer referência a uma coleção genérica de segurança crítica, um campo crítico de segurança e um método crítico de segurança.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>