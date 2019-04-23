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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 41e296a979557a42a96c2f57ce49610d88b98a40
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073158"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementar construtores de serialização
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ImplementSerializationConstructors|
|CheckId|CA2229|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 O tipo implementa o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> da interface, não é um delegado ou interface e uma das seguintes condições for verdadeira:

- O tipo não tem um construtor que usa um <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto e um <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objeto (a assinatura do construtor de serialização).

- O tipo é sem lacre e o modificador de acesso para seu construtor de serialização não é protegida (família).

- O tipo está lacrado e o modificador de acesso para seu construtor de serialização não é privado.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é relevante para tipos que oferecem suporte a serialização personalizada. Um tipo é compatível com a serialização personalizada se ele implementa o <xref:System.Runtime.Serialization.ISerializable> interface. O construtor de serialização é necessário para desserializar ou recriar objetos que foram serializados usando a <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima uma violação da regra. O tipo não serão desserializável e não funcionará em muitos cenários.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que satisfaça a regra.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
