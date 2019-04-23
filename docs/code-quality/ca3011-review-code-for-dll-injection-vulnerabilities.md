---
title: 'CA3011: Examinar código quanto a vulnerabilidades de injeção de DLL'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a6f3a2db89e35408a19cec47c971821fedf5f85a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089518"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011: Examinar código quanto a vulnerabilidades de injeção de DLL

|||
|-|-|
|NomeDoTipo|ReviewCodeForDllInjectionVulnerabilities|
|CheckId|CA3011|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Solicitação HTTP potencialmente não confiável entrada atinge um método que carrega um assembly.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis, lembre-se de carregar o código não confiável. Se seu aplicativo web for carregada em código não confiável, um invasor poderá injetar DLLs mal-intencionado no seu processo e executar código mal-intencionado.

Essa regra tenta encontrar a entrada de uma solicitação HTTP que atinja um método que carrega um assembly.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que carrega um assembly, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em `.editorconfig` arquivos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Não carregar as DLLs não confiáveis de entrada do usuário.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima avisos dessa regra.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
