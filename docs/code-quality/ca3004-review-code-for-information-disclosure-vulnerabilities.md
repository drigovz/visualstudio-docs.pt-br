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
ms.openlocfilehash: 82f763d9a6b1ec27975aa80054456a6bbbaeaa2b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069022"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Examinar código quanto a vulnerabilidades de divulgação de informações

|||
|-|-|
|NomeDoTipo|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Mensagem de uma exceção, rastreamento de pilha ou representação de cadeia de caracteres alcança a saída do web.

## <a name="rule-description"></a>Descrição da regra

Divulgação de informações de exceção fornece percepção dos recursos internos do seu aplicativo, que pode ajudar invasores a encontrar outras vulnerabilidades de exploração de invasores.

Essa regra tenta localizar uma mensagem de exceção, o rastreamento de pilha ou a representação de cadeia de caracteres, sendo a saída para uma resposta HTTP.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly de captura uma exceção e, em seguida, passa-o para outro assembly que gera a exceção, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em `.editorconfig` arquivos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Não informações de exceção para respostas HTTP de saída. Em vez disso, fornece uma mensagem de erro genérica. Ver [página de tratamento de erros do OWASP](https://www.owasp.org/index.php/Error_Handling) para obter mais diretrizes.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você souber que a saída da web está dentro do limite de confiança do seu aplicativo e nunca exposto fora, é okey suprimir este aviso. Isso é raro. Leve em consideração que o limite de confiança do seu aplicativo e fluxos de dados podem ser alterados ao longo do tempo.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

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