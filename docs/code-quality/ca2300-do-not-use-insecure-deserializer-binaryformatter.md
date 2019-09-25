---
title: 'CA2300: Não usar o desserializador BinaryFormatter não seguro'
ms.date: 04/05/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2300
- DoNotUseInsecureDeserializerBinaryFormatter
ms.openlocfilehash: 4ca4990308ceab21e2c6e256770ff37a3ca9a6fc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237949"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300: Não usar o desserializador BinaryFormatter não seguro

|||
|-|-|
|NomeDoTipo|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Categoria|Microsoft.Security|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> método de desserialização foi chamado ou referenciado.

## <a name="rule-description"></a>Descrição da regra

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Essa regra localiza <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> chamadas ou referências do método de desserialização. Se você quiser desserializar apenas quando a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriedade for definida para restringir tipos, desabilite essa regra e habilite as regras [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) em vez disso.

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Se possível, use um serializador seguro em vez disso e **não permita que um invasor especifique um tipo arbitrário para desserializar**. Alguns serializadores mais seguros incluem:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Nunca use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se você precisar usar um resolvedor de tipo, restrinja os tipos desserializados a uma lista esperada.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-use TypeNameHandling. None. Se você precisar usar outro valor para TypeNameHandling, restrinja os tipos desserializados a uma lista esperada com um ISerializationBinder personalizado.
  - Buffers de protocolo
- Torne a prova de adulteração dos dados serializados. Após a serialização, assine criptograficamente os dados serializados. Antes da desserialização, valide a assinatura criptográfica. Proteja a chave de criptografia de ser divulgada e design para rotações de chave.
- Restringir tipos desserializados. Implemente um <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>personalizado. Antes de desserializar <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>com, defina <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> a propriedade como uma instância de seu <xref:System.Runtime.Serialization.SerializationBinder>personalizado. No método substituído <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , se o tipo for inesperado, lance uma exceção para interromper a desserialização.
  - Se você restringir os tipos desserializados, talvez queira desabilitar essa regra e habilitar as regras [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). As regras [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) ajudam a garantir que <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> a propriedade seja sempre definida antes da desserialização.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Exemplos de pseudocódigo

### <a name="violation"></a>Infra

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Regras relacionadas

[CA2301: Não chame BinaryFormatter. desserializate sem primeiro configurar BinaryFormatter. Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Certifique-se de que BinaryFormatter. Binder esteja definido antes de chamar BinaryFormatter. desserializar](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)