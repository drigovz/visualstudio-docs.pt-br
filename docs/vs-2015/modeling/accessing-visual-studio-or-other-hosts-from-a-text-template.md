---
title: Acessando o Visual Studio 2015 ou outros hosts de um modelo de texto | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655333"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Acessando o Visual Studio ou outros hosts a partir de um modelo de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um modelo de texto, você pode usar métodos e propriedades expostos pelo host que executa o modelo, como [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Isso se aplica a modelos de texto comuns, não a modelos de texto pré-processados.

## <a name="obtaining-access-to-the-host"></a>Obtendo acesso ao host

Defina `hostspecific="true"` na diretiva `template`. Isso permite que você use `this.Host`, que tem o tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Esse tipo tem membros que você pode usar, por exemplo, para resolver nomes de arquivo e registrar erros.

### <a name="resolving-file-names"></a>Resolvendo nomes de arquivo
 Para localizar o caminho completo de um arquivo relativo ao modelo de texto, use-o. Host. ResolvePath ().

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

### <a name="displaying-error-messages"></a>Exibindo mensagens de erro
 Este exemplo registra mensagens quando você transforma o modelo. Se o host for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eles serão adicionados à janela de erro.

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

## <a name="using-the-visual-studio-api"></a>Usando a API do Visual Studio
 Se você estiver executando um modelo de texto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], poderá usar `this.Host` para acessar os serviços fornecidos pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e quaisquer pacotes ou extensões que estejam carregados.

 Defina hostspecific = "true" e converta `this.Host` para <xref:System.IServiceProvider>.

 Este exemplo obtém a API [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], <xref:EnvDTE.DTE>, como um serviço:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Usando hostSpecific com herança de modelo
 Especifique `hostspecific="trueFromBase"` se você também usar o atributo `inherits` e se herdar de um modelo que especifica `hostspecific="true"`. Isso evita um aviso do compilador para o efeito de que a propriedade `Host` foi declarada duas vezes.
