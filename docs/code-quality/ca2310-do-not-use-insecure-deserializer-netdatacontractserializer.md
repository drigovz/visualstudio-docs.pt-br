---
title: 'CA2310: Não use desserializador inseguro NetDataContractSerializer'
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
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135424"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Não use desserializador inseguro NetDataContractSerializer

|||
|-|-|
|NomeDoTipo|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> método de desserialização foi chamado ou referenciado.

## <a name="rule-description"></a>Descrição da regra

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Essa regra localiza <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> referências ou chamadas de método de desserialização. Se você deseja desserializar somente quando o <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> estiver definida como restringir tipos, desabilite essa regra e habilite regras [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) em vez disso.

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Se possível, use um serializador seguro em vez disso, e **não permitir que um invasor especificar um tipo arbitrário para desserializar**. Alguns serializadores mais seguros incluem:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nunca usar <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se você precisar usar um resolvedor de tipo, restringir tipos desserializados para uma lista de esperado.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET - TypeNameHandling.None de uso. Se você precisar usar outro valor para TypeNameHandling, restringir tipos desserializados para uma lista de esperado com um ISerializationBinder personalizado.
  - Buffers de protocolo
- Verifique a prova de adulteração de dados serializados. Após a serialização, assina criptograficamente os dados serializados. Antes de desserialização, valide a assinatura de criptografia. Protege a chave de criptografia do que está sendo divulgadas e design para rotações de chave.
- Restringir tipos desserializados. Implementar um personalizado <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Antes de desserializá-lo com <xref:System.Runtime.Serialization.NetDataContractSerializer>, defina a <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propriedade a uma instância do seu personalizado <xref:System.Runtime.Serialization.SerializationBinder>. No substituído <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> método, se o tipo for inesperado, lançar uma exceção.
- Se você restringir tipos desserializados, você talvez queira desabilitar essa regra e habilitar as regras [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). As regras [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) ajudam a garantir que o <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propriedade é sempre definida antes da desserialização.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

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

[CA2311: Não desserializar sem primeiro definir NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Verifique se que NetDataContractSerializer.Binder está definido antes de desserialização](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
