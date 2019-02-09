---
title: 'CA2239: Fornecer métodos de desserialização para campos opcionais'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5599f111d6580f654436fdd2ff85f69f1329920d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907523"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Fornecer métodos de desserialização para campos opcionais

|||
|-|-|
|NomeDoTipo|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo tem um campo que é marcado com o <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atributo e o tipo não fornece métodos de manipulação de eventos de desserialização.

## <a name="rule-description"></a>Descrição da regra
 O <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributo não tem nenhum efeito na serialização; um campo marcado com o atributo é serializado. No entanto, o campo é ignorado na desserialização e retém o valor padrão associado com seu tipo. Manipuladores de eventos de desserialização devem ser declarados para definir o campo durante o processo de desserialização.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, adicione métodos para o tipo de manipulação de evento de desserialização.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 É seguro suprimir um aviso nessa regra, se o campo deve ser ignorado durante o processo de desserialização.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra métodos de manipulação de um tipo com um campo opcional e o evento de desserialização.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2236: Chamar métodos da classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Construtores de serialização segura](../code-quality/ca2120-secure-serialization-constructors.md)