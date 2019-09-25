---
title: 'CA2236: Chamar métodos da classe base em tipos ISerializable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a9a3070abc1f2bab3f3658589db54b656a635e2b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238079"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Chamar métodos da classe base em tipos ISerializable

|||
|-|-|
|NomeDoTipo|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo deriva de um tipo que implementa a <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface e uma das seguintes condições é verdadeira:

- O tipo implementa o construtor de serialização, ou seja, um construtor com <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>a <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> assinatura de parâmetro, mas não chama o construtor de serialização do tipo base.

- O tipo implementa o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método, mas não chama o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método do tipo base.

## <a name="rule-description"></a>Descrição da regra
Em um processo de serialização personalizado, um tipo implementa <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> o método para serializar seus campos e o construtor de serialização para desserializar os campos. Se o tipo derivar de um tipo que implementa a <xref:System.Runtime.Serialization.ISerializable> interface, o método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> tipo base e o construtor de serialização deverão ser chamados para serializar/desserializar os campos do tipo base. Caso contrário, o tipo não será serializado e desserializado corretamente. Observe que, se o tipo derivado não adicionar nenhum novo campo, o tipo não precisará implementar o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método nem o construtor de serialização nem chamar os equivalentes de tipo base.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, chame o método de tipo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> base ou construtor de serialização do construtor ou método de tipo derivado correspondente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo derivado que satisfaz a regra chamando o construtor de serialização e <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> o método da classe base.

[!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
[!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2240: Implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Construtores de serialização segura](../code-quality/ca2120-secure-serialization-constructors.md)