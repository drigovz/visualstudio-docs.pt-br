---
title: 'CA2315: Não use desserializador inseguro ObjectStateFormatter'
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
- CA2315
- DoNotUseInsecureDeserializerObjectStateFormatter
ms.openlocfilehash: 793fa9df333eed7e485d7d8829849ae30d9c93a2
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135484"
---
# <a name="ca2315-do-not-use-insecure-deserializer-objectstateformatter"></a>CA2315: Não use desserializador inseguro ObjectStateFormatter

|||
|-|-|
|NomeDoTipo|DoNotUseInsecureDeserializerObjectStateFormatter|
|CheckId|CA2315|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um <xref:System.Web.UI.ObjectStateFormatter?displayProperty=nameWithType> método de desserialização foi chamado ou referenciado.

## <a name="rule-description"></a>Descrição da regra

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Essa regra localiza <xref:System.Web.UI.ObjectStateFormatter?displayProperty=nameWithType> referências ou chamadas de método de desserialização.

## <a name="how-to-fix-violations"></a>Como corrigir violações

[!INCLUDE[insecure-deserializers-fixes-for-always-insecure-deserializers](includes/insecure-deserializers-fixes-for-always-insecure-deserializers-md.md)]

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System.IO;
using System.Web.UI;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        ObjectStateFormatter formatter = new ObjectStateFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Web.UI

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As ObjectStateFormatter = New ObjectStateFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```