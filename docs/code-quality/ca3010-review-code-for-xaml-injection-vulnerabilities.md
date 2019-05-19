---
title: 'CA3010: Examinar código quanto a vulnerabilidades de injeção de XAML'
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
ms.openlocfilehash: 965e0d800bd7c725236d96499d2bf2d441b40412
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841098"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Examinar código quanto a vulnerabilidades de injeção de XAML

|||
|-|-|
|NomeDoTipo|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Solicitação HTTP potencialmente não confiável de entrada atinge um <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> método de carga.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis, lembre-se de ataques de injeção de XAML. XAML é uma linguagem de marcação que representa diretamente a instanciação e execução de objetos. Isso significa que os elementos criados em XAML podem interagir com recursos do sistema (por exemplo, acesso e o arquivo de sistema de rede e/s). Se um invasor pode controlar a entrada para um <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> carregar chamada de método, em seguida, o invasor pode executar o código.

Essa regra tenta encontrar a entrada de solicitações HTTP que atinja um <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> método de carga.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que carrega a XAML, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em um arquivo EditorConfig.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Não carregar o XAML não confiável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima avisos dessa regra.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
