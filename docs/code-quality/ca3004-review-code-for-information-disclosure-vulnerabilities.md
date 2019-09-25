---
title: 'CA3004: Examinar código quanto a vulnerabilidades de divulgação de informações'
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
ms.openlocfilehash: 4965c9df3c2256511b8e44de8d388a9155d0d8f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237373"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Examinar código quanto a vulnerabilidades de divulgação de informações

|||
|-|-|
|NomeDoTipo|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Categoria|Microsoft.Security|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Uma mensagem de exceção, rastreamento de pilha ou representação de cadeia de caracteres atinge a saída da Web.

## <a name="rule-description"></a>Descrição da regra

A divulgação de informações de exceção dá aos invasores insights sobre os internos do seu aplicativo, o que pode ajudar os invasores a encontrar outras vulnerabilidades a serem exploradas.

Essa regra tenta localizar uma mensagem de exceção, um rastreamento de pilha ou uma representação de cadeia de caracteres que está sendo saída para uma resposta HTTP.

> [!NOTE]
> Esta regra não pode rastrear dados entre assemblies. Por exemplo, se um assembly capturar uma exceção e, em seguida, passá-la para outro assembly que gera a exceção, essa regra não produzirá um aviso.

> [!NOTE]
> Há um limite configurável para o quão profundo essa regra irá analisar o fluxo de dados entre chamadas de método. Consulte [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em um arquivo EditorConfig.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Não gerar informações de exceção para respostas HTTP. Em vez disso, forneça uma mensagem de erro genérica. Consulte a [página de tratamento de erros do OWASP](https://www.owasp.org/index.php/Error_Handling) para obter mais diretrizes.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você souber que a saída da Web está dentro do limite de confiança do seu aplicativo e nunca exposta fora, não há problema em suprimir esse aviso. Isso é raro. Leve em consideração que o limite de confiança do seu aplicativo e os fluxos de dados podem mudar ao longo do tempo.

## <a name="pseudo-code-examples"></a>Exemplos de pseudocódigo

### <a name="violation"></a>Infra

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>Solução

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```