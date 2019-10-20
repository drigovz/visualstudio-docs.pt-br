---
title: Gerando arquivos com o utilitário TextTransform
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1a12da7c7cae7e862d670b3f62fb801920f34e1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666736"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Gerar arquivos com o utilitário TextTransform

TextTransform. exe é uma ferramenta de linha de comando que você pode usar para transformar um modelo de texto. Ao chamar TextTransform. exe, você especifica o nome de um arquivo de modelo de texto como um argumento. TextTransform. exe chama o mecanismo de transformação de texto e processa o modelo de texto. O TextTransform. exe é geralmente chamado a partir de scripts. No entanto, isso geralmente não é necessário, pois você pode executar a transformação de texto no Visual Studio ou no processo de compilação.

> [!NOTE]
> Se você quiser executar a transformação de texto como parte de um processo de compilação, considere usar a tarefa de transformação de texto do MSBuild. Para obter mais informações, consulte [geração de código em um processo de compilação](../modeling/code-generation-in-a-build-process.md). Em um computador no qual o Visual Studio está instalado, você também pode escrever um aplicativo ou uma extensão do Visual Studio que possa transformar modelos de texto. Para obter mais informações, consulte [processando modelos de texto usando um host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform. exe está localizado no seguinte diretório:

::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

para Professional Edition ou

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

para Enterprise Edition.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

para Professional Edition ou

**\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

para Enterprise Edition.

Nas versões anteriores do Visual Studio, o arquivo é encontrado no seguinte local:

**\Program Files (x86) \Common Files\Microsoft Shared\TextTemplating \{version}**

em que {Version} depende de qual versão anterior está instalada.

::: moniker-end

## <a name="syntax"></a>Sintaxe

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parâmetros

|**Argumento**|**Descrição**|
|-|-|
|`templateName`|Identifica o nome do arquivo de modelo que você deseja transformar.|

|**Opção**|**Descrição**|
|-|-|
|**-out** \<filename >|O arquivo no qual a saída da transformação é gravada.|
|**-r** \<assembly >|Um assembly usado para compilar e executar o modelo de texto.|
|**-u** \<namespace >|Um namespace que é usado para compilar o modelo.|
|**-I** \<includedirectory >|Um diretório que contém os modelos de texto incluídos no modelo de texto especificado.|
|**-P** \<referencepath >|Um diretório para pesquisar assemblies especificados no modelo de texto ou para usar a opção **-r** .<br /><br /> Por exemplo, para incluir assemblies usados para a API do Visual Studio, use<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >! \<className >! \<assemblyName&#124;codebase >|O nome, o nome completo do tipo e o assembly de um processador de diretiva que pode ser usado para processar diretivas personalizadas dentro do modelo de texto.|
|**-a** [processadorname]! [diretivo]! \<parameterName >! \<parameterValue >|Especifique um valor de parâmetro para um processador de diretiva. Se você especificar apenas o nome do parâmetro e o valor, o parâmetro estará disponível para todos os processadores de diretiva. Se você especificar um processador de diretiva, o parâmetro estará disponível somente para o processador especificado. Se você especificar um nome de diretiva, o parâmetro estará disponível somente quando a diretiva especificada estiver sendo processada.<br /><br /> Para acessar os valores de parâmetro de um processador de diretivas ou modelo de texto, use [ITextTemplatingEngineHost. ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). Em um modelo de texto, inclua `hostspecific` na diretiva de modelo e invoque a mensagem em `this.Host`. Por exemplo:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`<br /><br /> Sempre digite as marcas '! ', mesmo se você omitir os nomes de diretiva e do processador opcionais. Por exemplo:<br /><br /> `-a !!param!value`|
|**-h**|Fornece ajuda.|

## <a name="related-topics"></a>Tópicos relacionados

|Tarefa|Tópico|
|-|-|
|Gere arquivos em uma solução do Visual Studio.|[Geração de código no tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Grave processadores de diretivas para transformar suas próprias fontes de dados.|[Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md)|
|Escreva um host de modelagem de texto que permita que você invoque modelos de texto de seu próprio aplicativo.|[Processando modelos de texto usando um host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)|
