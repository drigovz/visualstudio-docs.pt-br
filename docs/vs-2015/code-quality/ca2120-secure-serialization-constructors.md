---
title: 'CA2120: construtores de serialização segura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b734a5de257273312e5125c5f481ff889cd33e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664748"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: proteger construtores de serialização
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|SecureSerializationConstructors|
|CheckId|CA2120|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O tipo implementa a interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, não é um delegate ou interface e é declarado em um assembly que permite chamadores parcialmente confiáveis. O tipo tem um construtor que usa um objeto <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> e um objeto <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (a assinatura do construtor de serialização). Esse construtor não é protegido por uma verificação de segurança, mas um ou mais dos construtores regulares no tipo é protegido.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é relevante para tipos que dão suporte à serialização personalizada. Um tipo oferece suporte à serialização personalizada se implementar a interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>. O construtor de serialização é necessário e é usado para desserializar ou recriar objetos que foram serializados usando o método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>. Como o construtor de serialização aloca e inicializa objetos, as verificações de segurança que estão presentes em construtores regulares também devem estar presentes no construtor de serialização. Se você violar essa regra, os chamadores que não podiam criar uma instância poderiam usar o construtor de serialização para fazer isso.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, proteja o construtor de serialização com as demandas de segurança que são idênticas àquelas que protegem outros construtores.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir uma violação da regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
