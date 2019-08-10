---
title: 'CA2229: Implementar construtores de serialização'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11dfa98bb348f874a2774454cc465fb80cb71750
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920160"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementar construtores de serialização

|||
|-|-|
|NomeDoTipo|ImplementSerializationConstructors|
|CheckId|CA2229|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
O tipo implementa a <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, não é um delegado ou interface, e uma das seguintes condições é verdadeira:

- O tipo não tem um construtor que usa um <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto e um <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objeto (a assinatura do construtor de serialização).

- O tipo não é lacrado e o modificador de acesso para seu construtor de serialização não é protegido (família).

- O tipo é lacrado e o modificador de acesso para seu construtor de serialização não é privado.

## <a name="rule-description"></a>Descrição da regra
Essa regra é relevante para tipos que dão suporte à serialização personalizada. Um tipo oferece suporte à serialização personalizada se ela <xref:System.Runtime.Serialization.ISerializable> implementar a interface. O construtor de serialização é necessário para desserializar ou recriar objetos que foram serializados usando o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir uma violação da regra. O tipo não será desserializável e não funcionará em muitos cenários.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que satisfaz a regra.

[!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>