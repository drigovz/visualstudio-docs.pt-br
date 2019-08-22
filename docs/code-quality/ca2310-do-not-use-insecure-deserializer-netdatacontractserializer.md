---
title: 'CA2310: Não usar o desserializador inseguro NetDataContractSerializer'
ms.date: 05/01/2019
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
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: 09496fd11945ec4d419cc215569a7436f96d71ec
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891144"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Não usar o desserializador inseguro NetDataContractSerializer

|||
|-|-|
|NomeDoTipo|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Categoria|Microsoft.Security|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> método de desserialização foi chamado ou referenciado.

## <a name="rule-description"></a>Descrição da regra

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Essa regra localiza <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> chamadas ou referências do método de desserialização. Se você quiser desserializar apenas quando a <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propriedade for definida para restringir tipos, desabilite essa regra e habilite as regras [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) em vez disso.

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Se possível, use um serializador seguro em vez disso e **não permita que um invasor especifique um tipo arbitrário para**desserializar. Alguns serializadores mais seguros incluem:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Nunca use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se você precisar usar um resolvedor de tipo, restrinja os tipos desserializados a uma lista esperada.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-use TypeNameHandling. None. Se você precisar usar outro valor para TypeNameHandling, restrinja os tipos desserializados a uma lista esperada com um ISerializationBinder personalizado.
  - Buffers de protocolo
- Torne a prova de adulteração dos dados serializados. Após a serialização, assine criptograficamente os dados serializados. Antes da desserialização, valide a assinatura criptográfica. Proteja a chave de criptografia de ser divulgada e design para rotações de chave.
- Restringir tipos desserializados. Implemente um <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>personalizado. Antes de desserializar <xref:System.Runtime.Serialization.NetDataContractSerializer>com, defina <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> a propriedade como uma instância de seu <xref:System.Runtime.Serialization.SerializationBinder>personalizado. No método substituído <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , se o tipo for inesperado, lance uma exceção para interromper a desserialização.
  - Se você restringir os tipos desserializados, talvez queira desabilitar essa regra e habilitar as regras [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). As regras [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) ajudam a garantir que <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> a propriedade seja sempre definida antes da desserialização.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Exemplos de pseudocódigo

### <a name="violation"></a>Infra

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Regras relacionadas

[CA2311: Não desserializar sem primeiro configurar o NetDataContractSerializer. Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Verifique se o NetDataContractSerializer. Binder está definido antes da desserialização](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
