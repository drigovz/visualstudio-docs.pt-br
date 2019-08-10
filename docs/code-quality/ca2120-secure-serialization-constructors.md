---
title: 'CA2120: Construtores de serialização seguros'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc7f4a82b9a75e4d189e969712472f06b4019b73
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920876"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Construtores de serialização seguros

|||
|-|-|
|NomeDoTipo|SecureSerializationConstructors|
|CheckId|CA2120|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
O tipo implementa a <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, não é um delegate ou interface, e é declarado em um assembly que permite chamadores parcialmente confiáveis. O tipo tem um construtor que usa um <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto e um <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objeto (a assinatura do construtor de serialização). Esse construtor não é protegido por uma verificação de segurança, mas um ou mais dos construtores regulares no tipo é protegido.

## <a name="rule-description"></a>Descrição da regra
Essa regra é relevante para tipos que dão suporte à serialização personalizada. Um tipo oferece suporte à serialização personalizada se ela <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> implementar a interface. O construtor de serialização é necessário e é usado para desserializar ou recriar objetos que foram serializados usando o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método. Como o construtor de serialização aloca e inicializa objetos, as verificações de segurança que estão presentes em construtores regulares também devem estar presentes no construtor de serialização. Se você violar essa regra, os chamadores que não podiam criar uma instância poderiam usar o construtor de serialização para fazer isso.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, proteja o construtor de serialização com as demandas de segurança que são idênticas àquelas que protegem outros construtores.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir uma violação da regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola a regra.

[!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>