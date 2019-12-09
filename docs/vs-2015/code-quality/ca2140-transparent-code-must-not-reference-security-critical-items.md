---
title: 'CA2140: o código transparent não deve fazer referência a itens críticos de segurança | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602863"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: o código transparente não deve fazer referência a itens críticos de segurança
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

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

## <a name="rule-description"></a>Descrição da Regra
 Um elemento de código que é marcado com o atributo <xref:System.Security.SecurityCriticalAttribute> é crítico para segurança. Um método transparente não pode usar um elemento crítico para segurança. Se um tipo transparente tentar usar um tipo crítico de segurança, <xref:System.TypeAccessException>, <xref:System.MethodAccessException> ou <xref:System.FieldAccessException> será gerado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, siga um destes procedimentos:

- Marque o elemento de código que usa o código crítico de segurança com o atributo <xref:System.Security.SecurityCriticalAttribute>

     \- ou -

- Remova o atributo <xref:System.Security.SecurityCriticalAttribute> dos elementos de código marcados como segurança crítica e, em vez disso, marque-os com o atributo <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityTransparentAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 Nos exemplos a seguir, um método transparente tenta fazer referência a uma coleção genérica de segurança crítica, um campo crítico de segurança e um método crítico de segurança.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
