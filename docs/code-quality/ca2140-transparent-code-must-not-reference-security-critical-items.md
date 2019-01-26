---
title: 'CA2140: O código transparente não deve referenciar itens críticos de segurança'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: a67bd5649bd0f3f06d30f14f233cf3501871c25b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55032985"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: O código transparente não deve referenciar itens críticos de segurança

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um método transparente:

- lida com um tipo de exceção de segurança críticas de segurança

- tem um parâmetro que está marcado como um tipo crítico de segurança

- tem um parâmetro genérico com um restrições de segurança críticas

- tem uma variável local de um tipo crítico de segurança

- referencia um tipo que está marcado como segurança crítico

- chama um método que está marcado como segurança crítico

- faz referência a um campo que está marcado como segurança crítico

- Retorna um tipo que está marcado como segurança crítico

## <a name="rule-description"></a>Descrição da regra

Um elemento de código que é marcado com o <xref:System.Security.SecurityCriticalAttribute> atributo é crítico para segurança. Um método transparente não pode usar um elemento crítico para segurança. Se um tipo transparente tentar usar um tipo crítico de segurança uma <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , ou <xref:System.FieldAccessException> é gerado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, siga um destes procedimentos:

- Marcar o elemento de código que usa o código crítico de segurança com o <xref:System.Security.SecurityCriticalAttribute> atributo

     \- ou -

- Remover o <xref:System.Security.SecurityCriticalAttribute> atributo dos elementos de código que são marcados como segurança crítica e em vez disso, marcá-los com o <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityTransparentAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo

Nos exemplos a seguir, um método transparente tenta fazer referência a uma coleção genérica críticos de segurança, um campo de segurança crítica e um método crítico de segurança.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>