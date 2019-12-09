---
title: 'CA2235: marcar todos os campos não serializáveis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 709bc3dea92752d9e18c3163fe43864f5896471c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666768"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: marcar todos os campos não serializáveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável.

## <a name="rule-description"></a>Descrição da Regra
 Um tipo serializável é aquele marcado com o atributo <xref:System.SerializableAttribute?displayProperty=fullName>. Quando o tipo é serializado, uma exceção <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> é gerada se um tipo contém um campo de instância de um tipo que não é serializável.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, aplique o atributo <xref:System.NonSerializedAttribute?displayProperty=fullName> ao campo que não é serializável.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Apenas suprimir um aviso dessa regra se um tipo <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> for declarado que permite que as instâncias do campo sejam serializadas e desserializadas.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra e um tipo que satisfaz a regra.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)
