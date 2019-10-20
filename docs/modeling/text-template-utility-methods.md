---
title: Métodos de utilitário do modelo de texto
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e6426ea57fbdbec6ec47a4f6348463b88b250e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605996"
---
# <a name="text-template-utility-methods"></a>Métodos de utilitário do modelo de texto

Há vários métodos que estão sempre disponíveis quando você escreve o código em um modelo de texto do Visual Studio. Esses métodos são definidos em <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Você também pode usar outros métodos e serviços fornecidos pelo ambiente de host em um modelo de texto regular (não pré-processado). Por exemplo, você pode resolver caminhos de arquivo, erros de log e obter serviços fornecidos pelo Visual Studio e por quaisquer pacotes carregados. Para obter mais informações, consulte [acessando o Visual Studio a partir de um modelo de texto](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Métodos de gravação

Você pode usar os métodos `Write()` e `WriteLine()` para acrescentar texto dentro de um bloco de código padrão, em vez de usar um bloco de código de expressão. Os dois blocos de código a seguir são funcionalmente equivalentes.

### <a name="code-block-with-an-expression-block"></a>Bloco de código com um bloco de expressão

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Bloco de código usando WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Talvez você ache útil usar um desses métodos de utilitário em vez de um bloco de expressões dentro de um bloco de código longo com estruturas de controle aninhadas.

Os métodos `Write()` e `WriteLine()` têm duas sobrecargas, uma que usa um único parâmetro de cadeia de caracteres e outra que usa uma cadeia de caracteres de formato composto, mais uma matriz de objetos para incluir na cadeia de caracteres (como o método `Console.WriteLine()`). Os dois usos a seguir de `WriteLine()` são funcionalmente equivalentes:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Métodos de recuo

Você pode usar métodos de recuo para formatar a saída do seu modelo de texto. A classe <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> tem uma propriedade de cadeia de caracteres de `CurrentIndent` que mostra o recuo atual no modelo de texto e um campo de `indentLengths` que é uma lista dos recuos que foram adicionados. Você pode adicionar um recuo com o método `PushIndent()` e subtrair um recuo com o método `PopIndent()`. Se você quiser remover todos os recuos, use o método `ClearIndent()`. O bloco de código a seguir mostra o uso desses métodos:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

Esse bloco de código produz a seguinte saída:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Métodos de erro e aviso

Você pode usar métodos de utilitário de erro e aviso para adicionar mensagens ao Lista de Erros do Visual Studio. Por exemplo, o código a seguir adicionará uma mensagem de erro à Lista de Erros.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Acesso ao host e ao provedor de serviços

A propriedade `this.Host` pode fornecer acesso às propriedades expostas pelo host que está executando o modelo. Para usar `this.Host`, você deve definir `hostspecific` atributo na diretiva `<@template#>`:

`<#@template ... hostspecific="true" #>`

O tipo de `this.Host` depende do tipo de host no qual o modelo está sendo executado. Em um modelo que está sendo executado no Visual Studio, você pode converter `this.Host` em `IServiceProvider` para obter acesso a serviços como o IDE. Por exemplo:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Usando um conjunto diferente de métodos de utilitário

Como parte do processo de geração de texto, o arquivo de modelo é transformado em uma classe, que é sempre nomeada `GeneratedTextTransformation`and herda de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Se você quiser usar um conjunto diferente de métodos em vez disso, poderá escrever sua própria classe e especificá-la na diretiva de modelo. Sua classe deve herdar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

Use a diretiva `assembly` para referenciar o assembly onde a classe compilada pode ser encontrada.