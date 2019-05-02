---
title: 'CA3006: Examinar código quanto a vulnerabilidades de injeção de comando de processo'
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
ms.openlocfilehash: da161e611ca1d802c8da16370907029233bfd785
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806502"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Examinar código quanto a vulnerabilidades de injeção de comando de processo

|||
|-|-|
|NomeDoTipo|ReviewCodeForProcessCommandInjectionVulnerabilities|
|CheckId|CA3006|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Entradas de solicitação HTTP potencialmente não confiáveis atinge um comando de processo.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis, lembre-se de ataques de injeção de comando. Um ataque de injeção de comando pode executar comandos mal-intencionados no sistema operacional subjacente, comprometer a segurança e a integridade do seu servidor.

Essa regra tenta encontrar a entrada de solicitações HTTP atingindo um comando de processo.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que inicia um processo, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em `.editorconfig` arquivos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Se possível, evite iniciar processos com base na entrada do usuário.
- Valide a entrada em relação a um conjunto conhecido de seguro de caracteres e comprimento.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você souber que a entrada foi validada ou escape para ficar seguro, é seguro suprimir este aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.Diagnostics;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Process p = Process.Start(input);
    }
}
```

```vb
Imports System
Imports System.Diagnostics

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs as EventArgs)
        Dim input As String = Me.Request.Form("in")
        Dim p As Process = Process.Start(input)
    End Sub
End Class
```
