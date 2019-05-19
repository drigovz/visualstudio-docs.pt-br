---
title: 'CA3007: Examinar código quanto a vulnerabilidades de redirecionamento aberto'
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
ms.openlocfilehash: e60d0fad1262138b57f079485bc7455e55c7ec25
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841339"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Examinar código quanto a vulnerabilidades de redirecionamento aberto

|||
|-|-|
|NomeDoTipo|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Entradas de solicitação HTTP potencialmente não confiáveis atinge um redirecionamento de resposta HTTP.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis, lembre-se de vulnerabilidades de redirecionamento aberto. Um invasor pode explorar uma vulnerabilidade de redirecionamento aberto para usar seu site para dar a aparência de uma URL legítimos, mas redirecionar um visitante insuspeito um phishing ou outra página da Web mal-intencionadas.

Essa regra tenta encontrar a entrada de solicitações HTTP atingindo uma URL de redirecionamento HTTP.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que responde com um redirecionamento HTTP, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em um arquivo EditorConfig.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Algumas abordagens para a correção de vulnerabilidades de redirecionamento aberto incluem:

- Não permita que os usuários iniciem redirecionamentos.
- Não permita que os usuários especifiquem a qualquer parte da URL em um cenário de redirecionamento.
- Restringir redireciona para um predefinido "lista de permissões" de URLs.
- Validar URLs de redirecionamento.
- Se aplicável, considere usar uma página de aviso de isenção quando os usuários estão sendo redirecionados fora do seu site.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você souber que você tiver validado a entrada para ser restrito a URLs pretendidas, é okey suprimir este aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
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
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
