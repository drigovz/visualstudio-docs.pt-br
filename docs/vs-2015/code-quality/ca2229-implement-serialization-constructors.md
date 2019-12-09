---
title: 'CA2229: Implementar construtores de serialização | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56d53717afc8cd966903e75f77e1745de0031745
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662838"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: implementar construtores de serialização
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ImplementSerializationConstructors|
|CheckId|CA2229|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 O tipo implementa a interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, não é um delegado ou interface, e uma das seguintes condições é verdadeira:

- O tipo não tem um construtor que usa um objeto <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> e um objeto <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (a assinatura do construtor de serialização).

- O tipo não é lacrado e o modificador de acesso para seu construtor de serialização não é protegido (família).

- O tipo é lacrado e o modificador de acesso para seu construtor de serialização não é privado.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é relevante para tipos que dão suporte à serialização personalizada. Um tipo oferece suporte à serialização personalizada se implementar a interface <xref:System.Runtime.Serialization.ISerializable>. O construtor de serialização é necessário para desserializar ou recriar objetos que foram serializados usando o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir uma violação da regra. O tipo não será desserializável e não funcionará em muitos cenários.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que satisfaz a regra.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
