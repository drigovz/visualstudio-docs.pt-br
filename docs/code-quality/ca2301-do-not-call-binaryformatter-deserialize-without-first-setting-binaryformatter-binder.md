---
title: 'CA2301: Não chame BinaryFormatter.Deserialize sem primeiro definir BinaryFormatter.Binder'
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
ms.openlocfilehash: 97c82c414b85cbc26e0b711a0da246f3838cf554
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367274"
---
# <a name="ca2301-do-not-call-binaryformatterdeserialize-without-first-setting-binaryformatterbinder"></a>CA2301: Não chame BinaryFormatter.Deserialize sem primeiro definir BinaryFormatter.Binder

|||
|-|-|
|NomeDoTipo|DoNotCallBinaryFormatterDeserializeWithoutFirstSettingBinaryFormatterBinder|
|CheckId|CA2301|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> método de desserialização foi chamado ou referenciado sem o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> conjunto de propriedades.

## <a name="rule-description"></a>Descrição da regra

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Essa regra localiza <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> referências, ou chamadas de método de desserialização quando <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> não tem seu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> definido. Se você quiser impedir qualquer desserialização com <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> independentemente do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriedade, desabilitar essa regra e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)e habilitar a regra [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Se possível, use um serializador seguro em vez disso, e **não permitir que um invasor especificar um tipo arbitrário para desserializar**. Alguns serializadores mais seguros incluem:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nunca usar <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se você precisar usar um resolvedor de tipo, você deve restringir tipos desserializados para uma lista de esperado.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET - TypeNameHandling.None de uso. Se você precisar usar outro valor para TypeNameHandling, você deve restringir tipos desserializados para uma lista de esperado.
  - Buffers de protocolo
- Verifique os dados serializados à prova de adulteração. Após a serialização, assina criptograficamente os dados serializados. Antes de desserialização, valide a assinatura de criptografia. Você deve proteger a chave de criptografia de estejam sendo divulgadas e deve projetar para rotações de chave.
- Restringir tipos desserializados. Implementar um personalizado <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Antes de desserializá-lo com <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, defina a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propriedade a uma instância do seu personalizado <xref:System.Runtime.Serialization.SerializationBinder>. No substituído <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> método, se o tipo for inesperado, lance uma exceção.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

- É seguro suprimir um aviso nessa regra, se você souber que a entrada é confiável. Considere a possibilidade de que os fluxos de dados e limites de confiança do seu aplicativo podem mudar ao longo do tempo.
- É seguro suprimir este aviso se você executou um das precauções acima.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Solução
```csharp
using System;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", "typeName");
        }
    }
}

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        formatter.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Runtime.Serialization.Formatters.Binary

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", "typeName")
        End If
    End Function
End Class

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        formatter.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Regras relacionadas

[CA2300: Não use desserializador inseguro BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2302: Verifique se que BinaryFormatter.Binder está definido antes de chamar BinaryFormatter.Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)