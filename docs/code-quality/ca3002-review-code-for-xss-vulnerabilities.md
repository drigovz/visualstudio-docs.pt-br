---
title: 'CA3002: Examinar código quanto a vulnerabilidades de XSS'
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
ms.openlocfilehash: 383011e53b14ec2cc7dd7474cd050f05295a2a73
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841465"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Examinar código quanto a vulnerabilidades de XSS

|||
|-|-|
|NomeDoTipo|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Entradas de solicitação HTTP potencialmente não confiáveis alcança a saída HTML bruta.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis de solicitações da web, lembre-se de ataques de (XSS) scripts entre sites. Um ataque XSS injeta entradas não confiáveis em HTML bruto de saída, permitindo que o invasor execute scripts mal-intencionados ou maliciosamente modificar o conteúdo em sua página da web. Uma técnica comum é colocar `<script>` elementos com um código mal-intencionado na entrada. Para obter mais informações, consulte [XSS do OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Essa regra tenta encontrar a entrada de solicitações HTTP atingindo saída bruta do HTML.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que gera o HTML bruto, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em um arquivo EditorConfig.

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Em vez de produzir HTML bruto, use um método ou propriedade que primeiro codifica em HTML sua entrada.
- A codificação HTML de dados não confiáveis antes de produzir HTML bruto.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra se:
- Você sabe que a entrada é validada em relação a um conjunto conhecido de seguro de caracteres que não contêm HTML.
- Você sabe que os dados são codificados em HTML de forma que não são detectada por essa regra.

> [!NOTE]
> Essa regra pode relatar falsos positivos para alguns métodos ou propriedades que a codificação HTML sua entrada.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>Solução

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```