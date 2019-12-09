---
title: 'CA2236: chamar métodos de classe base em tipos ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1d06d4acff24b724388e36de66038f563b1f5dc6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666704"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: chamar métodos de classe base em tipos ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo deriva de um tipo que implementa a interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> e uma das seguintes condições é verdadeira:

- O tipo implementa o construtor de serialização, ou seja, um construtor com a assinatura de parâmetro <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, mas não chama o construtor de serialização do tipo base.

- O tipo implementa o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>, mas não chama o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> do tipo base.

## <a name="rule-description"></a>Descrição da Regra
 Em um processo de serialização personalizado, um tipo implementa o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> para serializar seus campos e o construtor de serialização para desserializar os campos. Se o tipo derivar de um tipo que implementa a interface <xref:System.Runtime.Serialization.ISerializable>, o tipo de base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método e o construtor de serialização devem ser chamados para serializar/desserializar os campos do tipo base. Caso contrário, o tipo não será serializado e desserializado corretamente. Observe que, se o tipo derivado não adicionar nenhum novo campo, o tipo não precisará implementar o método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nem o construtor de serialização nem chamar os equivalentes de tipo base.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, chame o tipo de base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método ou construtor de serialização do método ou construtor de tipo derivado correspondente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo derivado que satisfaz a regra chamando o construtor de serialização e <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método da classe base.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2240: implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)
