---
title: Diretiva de parâmetro T4
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f833eb651efda0edb837515e1bf2b3567e1a759
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591795"
---
# <a name="t4-parameter-directive"></a>Diretiva de parâmetro T4

Em um modelo de texto do Visual Studio, a diretiva `parameter` declara Propriedades em seu código de modelo que são inicializadas a partir de valores passados do contexto externo. Você pode definir esses valores se escrever um código que invoque a transformação de texto.

## <a name="using-the-parameter-directive"></a>Usando a diretiva de parâmetro

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 A diretiva `parameter` declara Propriedades em seu código de modelo que são inicializadas a partir de valores passados do contexto externo. Você pode definir esses valores se escrever um código que invoque a transformação de texto. Os valores podem ser passados no dicionário de `Session` ou em <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Você pode declarar parâmetros de qualquer tipo remoto. Ou seja, o tipo deve ser declarado com <xref:System.SerializableAttribute>ou deve derivar de <xref:System.MarshalByRefObject>. Isso permite que os valores de parâmetro sejam passados para o AppDomain no qual o modelo é processado.

 Por exemplo, você pode escrever um modelo de texto com o seguinte conteúdo:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Passando valores de parâmetro para um modelo
 Se você estiver escrevendo uma extensão do Visual Studio, como um comando de menu ou um manipulador de eventos, poderá processar um modelo usando o serviço de modelagem de texto:

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));
```

## <a name="passing-values-in-the-call-context"></a>Passando valores no contexto da chamada
 Como alternativa, você pode passar valores como dados lógicos em <xref:System.Runtime.Remoting.Messaging.CallContext>.

 O exemplo a seguir passa valores usando os dois métodos:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test
```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Passando valores para um modelo de texto de tempo de execução (pré-processado)
 Normalmente, não é necessário usar a diretiva `<#@parameter#>` com modelos de texto de tempo de execução (pré-processados). Em vez disso, você pode definir um Construtor adicional ou uma propriedade settable para o código gerado, por meio do qual você passa valores de parâmetro. Para obter mais informações, consulte [geração de texto em tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 No entanto, se você quiser usar `<#@parameter>` em um modelo de tempo de execução, poderá passar valores para ele usando o dicionário de sessão. Como exemplo, suponha que você criou o arquivo como um modelo pré-processado chamado `PreTextTemplate1`. Você pode invocar o modelo em seu programa usando o código a seguir.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Obtendo argumentos de TextTemplate. exe

> [!IMPORTANT]
> A diretiva `parameter` não recupera valores definidos no parâmetro `-a` do utilitário `TextTransform.exe`. Para obter esses valores, defina `hostSpecific="true"` na diretiva `template` e use `this.Host.ResolveParameterValue("","","argName")`.
