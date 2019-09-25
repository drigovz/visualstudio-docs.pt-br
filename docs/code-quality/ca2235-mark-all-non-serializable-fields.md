---
title: 'CA2235: Marcar todos os campos não serializáveis'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238109"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Marcar todos os campos não serializáveis

|||
|-|-|
|NomeDoTipo|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável.

## <a name="rule-description"></a>Descrição da regra

Um tipo serializável é aquele marcado com o <xref:System.SerializableAttribute?displayProperty=fullName> atributo. Quando o tipo é serializado, uma <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> exceção é gerada se o tipo contém um campo de instância de um tipo que não é serializável *e* não <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> implementa a interface.

> [!TIP]
> CA2235 não é acionado por campos de instância de tipos <xref:System.Runtime.Serialization.ISerializable> que implementam porque fornecem sua própria lógica de serialização.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, aplique o <xref:System.NonSerializedAttribute?displayProperty=fullName> atributo ao campo que não é serializável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Apenas suprimir um aviso dessa regra se um <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> tipo for declarado que permite que instâncias do campo sejam serializadas e desserializadas.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra dois tipos: um que viola a regra e outra que satisfaça a regra.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Comentários

A regra CA2235 não analisa os tipos que implementam a <xref:System.Runtime.Serialization.ISerializable> interface (a menos que também sejam marcadas com o <xref:System.SerializableAttribute> atributo). Isso ocorre porque a [regra CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) já recomenda tipos de marcação que implementam a <xref:System.Runtime.Serialization.ISerializable> interface com o <xref:System.SerializableAttribute> atributo.

## <a name="related-rules"></a>Regras relacionadas

- [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Construtores de serialização segura](../code-quality/ca2120-secure-serialization-constructors.md)