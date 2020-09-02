---
title: Métodos de utilitário do modelo de texto
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55da4d58b717bc4d42b6fafdd084067b7e21a31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591756"
---
# <a name="text-template-utility-methods"></a>Métodos de utilitário do modelo de texto

Há vários métodos que estão sempre disponíveis quando você escreve o código em um modelo de texto do Visual Studio. Esses métodos são definidos em <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Você também pode usar outros métodos e serviços fornecidos pelo ambiente de host em um modelo de texto regular (não pré-processado). Por exemplo, você pode resolver caminhos de arquivo, erros de log e obter serviços fornecidos pelo Visual Studio e por quaisquer pacotes carregados. Para obter mais informações, consulte [acessando o Visual Studio a partir de um modelo de texto](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Métodos de gravação

Você pode usar os `Write()` `WriteLine()` métodos e para acrescentar texto dentro de um bloco de código padrão, em vez de usar um bloco de código de expressão. Os dois blocos de código a seguir são funcionalmente equivalentes.

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

Os `Write()` `WriteLine()` métodos e têm duas sobrecargas, uma que usa um único parâmetro de cadeia de caracteres e outra que usa uma cadeia de caracteres de formato composto, além de uma matriz de objetos para incluir na cadeia de caracteres (como o `Console.WriteLine()` método). Os dois usos a seguir do `WriteLine()` são funcionalmente equivalentes:

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

Você pode usar métodos de recuo para formatar a saída do seu modelo de texto. A <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> classe tem uma `CurrentIndent` propriedade de cadeia de caracteres que mostra o recuo atual no modelo de texto e um `indentLengths` campo que é uma lista dos recuos que foram adicionados. Você pode adicionar um recuo com o `PushIndent()` método e subtrair um recuo com o `PopIndent()` método. Se você quiser remover todos os recuos, use o `ClearIndent()` método. O bloco de código a seguir mostra o uso desses métodos:

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

A propriedade `this.Host` pode fornecer acesso às propriedades expostas pelo host que está executando o modelo. Para usar `this.Host` o, você deve definir `hostspecific` o atributo na `<@template#>` diretiva:

`<#@template ... hostspecific="true" #>`

O tipo de `this.Host` depende do tipo de host no qual o modelo está sendo executado. Em um modelo que está sendo executado no Visual Studio, você pode converter `this.Host` para `IServiceProvider` para obter acesso a serviços como o IDE. Por exemplo:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Usando um conjunto diferente de métodos de utilitário

Como parte do processo de geração de texto, o arquivo de modelo é transformado em uma classe, que é sempre nomeada `GeneratedTextTransformation` e herdada de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Se você quiser usar um conjunto diferente de métodos em vez disso, poderá escrever sua própria classe e especificá-la na diretiva de modelo. Sua classe deve herdar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Use a `assembly` diretiva para referenciar o assembly onde a classe compilada pode ser encontrada.
