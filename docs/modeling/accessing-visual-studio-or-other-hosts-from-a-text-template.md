---
title: Acessando o Visual Studio ou outros hosts a partir de um modelo de texto
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652369"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Acessar o Visual Studio ou outros hosts de um modelo de texto

Em um modelo de texto, você pode usar métodos e propriedades que são expostos pelo host que executa o modelo. O Visual Studio é um exemplo de um host.

> [!NOTE]
> Você pode usar métodos e propriedades de host em modelos de texto comuns, mas não em modelos de texto *pré-processados* .

## <a name="obtain-access-to-the-host"></a>Obter acesso ao host

Para acessar o host, defina `hostspecific="true"` na diretiva `template`. Agora você pode usar `this.Host`, que tem o tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). O tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) tem membros que você pode usar para resolver nomes de arquivo e erros de log, por exemplo.

### <a name="resolve-file-names"></a>Resolver nomes de arquivo

Para localizar o caminho completo de um arquivo relativo ao modelo de texto, use `this.Host.ResolvePath()`.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Exibir mensagens de erro

Este exemplo registra mensagens quando você transforma o modelo. Se o host for o Visual Studio, os erros serão adicionados à **lista de erros**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Usar a API do Visual Studio

Se você estiver executando um modelo de texto no Visual Studio, poderá usar `this.Host` para acessar os serviços fornecidos pelo Visual Studio e quaisquer pacotes ou extensões que estejam carregados.

Defina hostspecific = "true" e converta `this.Host` para <xref:System.IServiceProvider>.

Este exemplo obtém a API do Visual Studio, <xref:EnvDTE.DTE> como um serviço:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Usar hostSpecific com herança de modelo

Especifique `hostspecific="trueFromBase"` se você também usar o atributo `inherits` e se herdar de um modelo que especifica `hostspecific="true"`. Caso contrário, você pode obter um compilador avisando que a propriedade `Host` foi declarada duas vezes.