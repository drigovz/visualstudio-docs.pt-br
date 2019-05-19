---
title: 'CA3012: Examinar código quanto a vulnerabilidades de injeção de regex'
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
ms.openlocfilehash: b66e28804e85b04b1492a20828c42a9b5efd3cf8
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841047"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Examinar código quanto a vulnerabilidades de injeção de regex

|||
|-|-|
|NomeDoTipo|ReviewCodeForRegexInjectionVulnerabilities|
|CheckId|CA3012|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Entradas de solicitação HTTP potencialmente não confiáveis atinge uma expressão regular.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis, lembre-se de ataques de injeção de regex. Um invasor pode usar a injeção de regex de maneira mal-intencionada modificar uma expressão regular, para tornar o regex corresponderem aos resultados não intencionais ou fazer com que o regex consomem CPU excessiva, resultando em um ataque de negação de serviço.

Essa regra tenta encontrar a entrada de solicitações HTTP atingindo uma expressão regular.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que cria uma expressão regular, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em um arquivo EditorConfig.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Algumas mitigações contra injeções de regex incluem:

- Sempre use uma [corresponde ao tempo limite](/dotnet/standard/base-types/best-practices#use-time-out-values) ao usar expressões regulares.
- Evite usar expressões regulares com base na entrada do usuário.
- Escapar caracteres especiais de entrada do usuário chamando <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> ou outro método.
- Permitir caracteres de apenas não especial da entrada do usuário.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você souber que você está usando um [corresponde ao tempo limite](/dotnet/standard/base-types/best-practices#use-time-out-values) e a entrada do usuário é livre de caracteres especiais, é okey suprimir este aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
