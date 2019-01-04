---
title: 'CA2240: Implementar ISerializable corretamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 966e92b7973ee22ce4da2be7edb1cc075c42077a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868359"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementar ISerializable corretamente

|||
|-|-|
|NomeDoTipo|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um tipo visível externamente é atribuível para o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface e uma das seguintes condições é verdadeira:

- O tipo herda, mas não substitui o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método e o tipo declara campos de instância que não são marcados com o <xref:System.NonSerializedAttribute?displayProperty=fullName> atributo.

- O tipo não está lacrado e o tipo implementa um <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método que não seja externamente visível e substituível.

## <a name="rule-description"></a>Descrição da regra
 Campos que são declarados em um tipo que herda de instância a <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface não são incluídos automaticamente no processo de serialização. Para incluir os campos, o tipo deve implementar o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método e o construtor de serialização. Se os campos não devem ser serializados, aplique o <xref:System.NonSerializedAttribute> para os campos para indicar explicitamente a decisão de atributo.

 Em tipos que não são seladas, implementações do <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser visível externamente. Portanto, o método pode ser chamado por tipos derivados e é substituível.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, verifique as <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método visível e substituível e verifique se todos os campos de instância são incluídos no processo de serialização ou marcados explicitamente com o <xref:System.NonSerializedAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois tipos serializáveis que violam a regra.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige as duas violações anteriores, fornecendo uma implementação substituível do <xref:System.Runtime.Serialization.ISerializable.GetObjectData> na classe livro e fornecendo uma implementação de `GetObjectData` na classe de biblioteca.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA2236: Chamar métodos da classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Construtores de serialização segura](../code-quality/ca2120-secure-serialization-constructors.md)