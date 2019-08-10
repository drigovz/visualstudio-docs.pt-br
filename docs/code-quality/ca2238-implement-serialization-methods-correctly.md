---
title: 'CA2238: Implementar métodos de serialização corretamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ec40eb3317f541bec92f06d8921fc2f545606d1a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920080"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementar métodos de serialização corretamente

|||
|-|-|
|NomeDoTipo|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra-se o método é visível fora do assembly.<br /><br /> Não separável – se o método não estiver visível fora do assembly.|

## <a name="cause"></a>Causa
Um método que trata um evento de serialização não tem a assinatura, o tipo de retorno ou a visibilidade corretos.

## <a name="rule-description"></a>Descrição da regra
Um método é designado como um manipulador de eventos de serialização aplicando um dos seguintes atributos de evento de serialização:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Os manipuladores de eventos de serialização assumem um <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>único parâmetro `void`de tipo, `private` retorno e têm visibilidade.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, corrija a assinatura, o tipo de retorno ou a visibilidade do manipulador de eventos de serialização.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra os manipuladores de eventos de serialização declarados corretamente.

[!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
[!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2236: Chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Construtores de serialização segura](../code-quality/ca2120-secure-serialization-constructors.md)