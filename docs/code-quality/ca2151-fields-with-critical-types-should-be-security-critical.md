---
title: 'CA2151: Campos com tipos críticos devem ser críticos para segurança'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 938d080aa61f8370be00069aa9399b195d31d296
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001297"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: Campos com tipos críticos devem ser críticos para segurança

|||
|-|-|
|NomeDoTipo||
|CheckId|CA2151|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um campo transparente de segurança ou um campo de segurança crítica é declarado. O tipo é especificado como de segurança crítica. Por exemplo:

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

Neste exemplo, `m_field` é um campo transparente de segurança de um tipo de segurança crítica.

## <a name="rule-description"></a>Descrição da regra

Para usar tipos de segurança crítica, o código que faz referência ao tipo deve ser de segurança crítica ou de segurança crítica segura. Isso será verdadeiro mesmo que a referência seja indireta. Por exemplo, ao fazer referência a um campo transparente de tipo crítico, o código deve ser de segurança crítica ou de segurança. Por isso, ter um campo de segurança transparente ou de segurança crítica é enganoso porque o código transparente continuará incapaz de acessar o campo.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, marque o campo com o <xref:System.Security.SecurityCriticalAttribute> de atributo ou tornar o tipo que é referenciado pelo campo qualquer segurança transparente ou crítica.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]