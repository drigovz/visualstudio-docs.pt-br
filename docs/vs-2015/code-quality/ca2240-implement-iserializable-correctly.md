---
title: 'CA2240: implementar ISerializable corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0abc95811dc870abbfaa583fbaa7705302a70781
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670164"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: implementar ISerializable corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo visível externamente é atribuível à interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> e uma das seguintes condições é verdadeira:

- O tipo é herdado, mas não substitui o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> e o tipo declara os campos de instância que não estão marcados com o atributo <xref:System.NonSerializedAttribute?displayProperty=fullName>.

- O tipo não é lacrado e o tipo implementa um método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> que não é visível externamente e substituível.

## <a name="rule-description"></a>Descrição da Regra
 Os campos de instância que são declarados em um tipo que herdam a interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> não são incluídos automaticamente no processo de serialização. Para incluir os campos, o tipo deve implementar o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> e o construtor de serialização. Se os campos não devem ser serializados, aplique o atributo <xref:System.NonSerializedAttribute> aos campos para indicar explicitamente a decisão.

 Em tipos que não são lacrados, as implementações do método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> devem ser visíveis externamente. Portanto, o método pode ser chamado por tipos derivados e é substituível.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, torne o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> visível e substituível e verifique se todos os campos de instância estão incluídos no processo de serialização ou explicitamente marcados com o atributo <xref:System.NonSerializedAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois tipos serializáveis que violam a regra.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige as duas violações anteriores fornecendo uma implementação substituível de [ISerializable. GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) na classe Book e fornecendo uma implementação de <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> na classe de biblioteca.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)
