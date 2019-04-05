---
title: 'CA3008: Examine o código para vulnerabilidades de injeção de XPath'
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
ms.openlocfilehash: e66b75160df0e8ecf9d33601ee383ec71cd62c4d
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018449"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: Examine o código para vulnerabilidades de injeção de XPath

|||
|-|-|
|NomeDoTipo|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Entradas de solicitação HTTP potencialmente não confiáveis atinge uma consulta XPath.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis, lembre-se de ataques de injeção de XPath. Construir consultas de XPath usando entradas não confiáveis pode permitir que um invasor maliciosamente manipular a consulta para retornar um resultado não intencional e, possivelmente, divulgue o conteúdo do XML consultado. 

Essa regra tenta encontrar a entrada de solicitações HTTP atingindo uma expressão XPath.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que executa uma consulta XPath, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em `.editorconfig` arquivos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Algumas abordagens para corrigir as vulnerabilidades de injeção de XPath incluem:

- Não construa consultas XPath de entrada do usuário.
- Valide que a entrada contém apenas um conjunto seguro de caracteres.
- Aspas de escape.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você souber que você tiver validado a entrada para ficar seguro, é okey suprimir este aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")
        
        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
