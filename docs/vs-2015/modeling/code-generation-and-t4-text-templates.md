---
title: Modelos de texto de geração de código e T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f34422dfd47efdce9bf837f923da0e139a13398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667915"
---
# <a name="code-generation-and-t4-text-templates"></a>Geração de código e modelos de texto T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , um *modelo de texto T4* é uma mistura de blocos de texto e lógica de controle que pode gerar um arquivo de texto. A lógica de controle é escrita como fragmentos de código de programa no [!INCLUDE[csprcs](../includes/csprcs-md.md)] ou no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . No Visual Studio 2015 atualização 2 e posterior, você pode usar os recursos da versão 6,0 do C# em diretivas de modelos T4. O arquivo gerado pode ser um texto de qualquer tipo, como uma página da Web, um arquivo de recurso ou um código-fonte do programa em qualquer idioma.

 Há dois tipos de modelos de texto T4:

 Os **modelos de texto T4 de tempo de execução** (modelos ' pré-processados ') são executados em seu aplicativo para produzir cadeias de caracteres de texto, normalmente como parte de sua saída.
Por exemplo, você pode criar um modelo para definir uma página HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

 Observe que o modelo se assemelha à saída gerada. A similaridade do modelo para a saída resultante ajuda a evitar erros quando você deseja alterá-lo.

 Além disso, o modelo contém fragmentos do código do programa. Você pode usar esses fragmentos para repetir seções de texto, para fazer seções condicionais e para mostrar dados de seu aplicativo.

 Para gerar a saída, seu aplicativo chama uma função que é gerada pelo modelo. Por exemplo:

```csharp
string webResponseText = new MyTemplate().TransformText();

```

 Seu aplicativo pode ser executado em um computador que não tenha o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalado.

 Para criar um modelo de tempo de execução, adicione um arquivo de **modelo de texto pré-processado** ao seu projeto. Como alternativa, você pode adicionar um arquivo de texto sem formatação e definir sua propriedade de **ferramenta personalizada** como **TextTemplatingFilePreprocessor**.

 Para obter mais informações, consulte [geração de texto em tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Para obter mais informações sobre a sintaxe de modelos, consulte [escrevendo um modelo de texto T4](../modeling/writing-a-t4-text-template.md).

 **Modelos de texto T4 de tempo de design** são executados no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para definir parte do código-fonte e outros recursos do seu aplicativo.
Normalmente, você usaria vários modelos que lêem os dados em um único arquivo de entrada ou banco de dado, além de gerar alguns dos seus `.cs` , `.vb` ou outros arquivos de origem. Cada modelo gera um arquivo. Eles são executados dentro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .

 Por exemplo, os dados de entrada podem ser um arquivo XML de dados de configuração. Sempre que você editar o arquivo XML durante o desenvolvimento, os modelos de texto regenerarão parte do código do aplicativo. Um dos modelos pode ser semelhante ao exemplo a seguir:

```
<#@ output extension=".txt" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}

```

 Dependendo dos valores no arquivo XML, o `.cs` arquivo gerado seria semelhante ao seguinte:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

 Como outro exemplo, a entrada pode ser um diagrama de fluxo de trabalho em uma atividade de negócios. Quando os usuários alteram seu fluxo de trabalho de negócios, ou quando você começa a trabalhar com novos usuários que têm um Workflow diferente, é fácil regenerar o código para se ajustar ao novo modelo.

 Os modelos de tempo de design tornam mais rápido e mais confiável alterar a configuração quando os requisitos mudam. Normalmente, a entrada é definida em termos de requisitos de negócios, como no exemplo de fluxo de trabalho. Isso facilita a discussão sobre as alterações com seus usuários. Os modelos de tempo de design são, portanto, uma ferramenta útil em um processo de desenvolvimento ágil.

 Para criar um modelo de tempo de design, adicione um arquivo de **modelo de texto** ao seu projeto. Como alternativa, você pode adicionar um arquivo de texto sem formatação e definir sua propriedade de **ferramenta personalizada** como **TextTemplatingFileGenerator**.

 Para obter mais informações, consulte [geração de código em tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Para obter mais informações sobre a sintaxe de modelos, consulte [escrevendo um modelo de texto T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> O termo *modelo* é, às vezes, usado para descrever os dados lidos por um ou mais modelos. O modelo pode estar em qualquer formato, em qualquer tipo de arquivo ou banco de dados. Ele não precisa ser um modelo UML ou um modelo de linguagem específico de domínio. ' Model ' indica apenas que os dados podem ser definidos em termos dos conceitos comerciais, em vez de se lembrar do código.

 O recurso de transformação de modelo de texto se chama *T4*.

## <a name="in-this-section"></a>Nesta seção
 [Geração de texto em tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md) Em qualquer aplicativo que gera arquivos de texto, os modelos de texto pré-compilados são um método fácil e confiável de definir o texto. No entanto, esse método não pode ser usado para modelos de texto que são alterados em tempo de execução.

 [Geração de código em tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Gerar código e outros recursos de um modelo permite que você atualize seu aplicativo atualizando o modelo.

 [Geração de código em um processo de compilação](../modeling/code-generation-in-a-build-process.md) Se você tiver instalado [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o SDK de visualização e modelagem, poderá garantir que o software gerado fique atualizado com as alterações no modelo.

 [Escrevendo um modelo de texto T4](../modeling/writing-a-t4-text-template.md) A sintaxe de um arquivo de modelo de texto.

 [Walkthrough: gerando código usando modelos de texto](../modeling/walkthrough-generating-code-by-using-text-templates.md) Uma demonstração de uma maneira de usar a geração de código.

 [Depurando um modelo de texto T4](../modeling/debugging-a-t4-text-template.md) Como depurar modelos de texto e alguns erros comuns de modelo de texto.

 [Gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) A ferramenta de linha de comando que você pode usar para executar transformações de modelo de texto.

 [Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md) Como escrever processadores de diretriz e hosts de modelagem personalizados para suas próprias fontes de dados.

## <a name="see-also"></a>Consulte Também
 [Gerar arquivos de um modelo UML](../modeling/generate-files-from-a-uml-model.md) que [gera código de uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)
