---
title: 'CA2237: Marcar tipos ISerializable com SerializableAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4a047ec190652e3559e8bf83fe14834ed95d8a69
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920106"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Marcar tipos ISerializable com SerializableAttribute

|||
|-|-|
|NomeDoTipo|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo visível externamente implementa a <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface e o tipo não é marcado com o <xref:System.SerializableAttribute?displayProperty=fullName> atributo. A regra ignora tipos derivados cujo tipo base não é serializável.

## <a name="rule-description"></a>Descrição da regra
Para ser reconhecido pelo Common Language Runtime como serializável, os tipos devem ser marcados com <xref:System.SerializableAttribute> o atributo, mesmo que o tipo use uma rotina <xref:System.Runtime.Serialization.ISerializable> de serialização personalizada por meio da implementação da interface.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, aplique o <xref:System.SerializableAttribute> atributo ao tipo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir um aviso desta regra para classes de exceção porque elas devem ser serializáveis para funcionar corretamente entre domínios de aplicativo.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola a regra. Remova a marca <xref:System.SerializableAttribute> de comentário da linha de atributo para atender à regra.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2236: Chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Construtores de serialização segura](../code-quality/ca2120-secure-serialization-constructors.md)