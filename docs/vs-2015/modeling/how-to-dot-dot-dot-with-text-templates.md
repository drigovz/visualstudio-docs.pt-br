---
title: Como... com modelos de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c55c7a277d3f38b36367008ae6393f58c9c9a2c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671622"
---
# <a name="how-to--with-text-templates"></a>Como ... com modelos de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os modelos de texto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornecem uma maneira útil de gerar texto de qualquer tipo. Você pode usar modelos de texto para gerar texto em tempo de execução como parte de seu aplicativo e em tempo de design para gerar parte do código do projeto. Este tópico resume as perguntas mais frequentes sobre "Como fazer...?" dúvidas.

 Neste tópico, várias respostas precedidas por marcadores são sugestões alternativas.

 Para obter uma introdução geral aos modelos de texto, leia [modelos de texto de geração de código e T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Como…

### <a name="generate-part-of-my-application-code"></a>Gerar parte do meu código do aplicativo
 Tenho uma configuração ou um *modelo* em um arquivo ou banco de dados. Uma ou mais partes do meu código dependem desse modelo.

- Gere alguns dos seus arquivos de código a partir de modelos de texto. Para obter mais informações, consulte [geração de código em tempo de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) e [qual é a melhor maneira de começar a escrever um modelo?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Gerar arquivos em tempo de execução, passando dados para o modelo
 Em tempo de execução, meu aplicativo gera arquivos de texto, como relatórios, que contêm uma mistura de texto e dados padrão. Quero evitar escrever centenas de `write` instruções.

- Adicione um modelo de texto de tempo de execução ao seu projeto. Este modelo cria uma classe em seu código, que você pode instanciar e usar para gerar texto. Você pode passar dados para ele nos parâmetros do construtor. Para obter mais informações, consulte [geração de texto em tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Se você quiser gerar a partir de modelos que estão disponíveis somente em tempo de execução, você pode usar modelos de texto padrão. Se você estiver escrevendo uma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensão, poderá invocar o serviço de modelagem de texto. Para obter mais informações, consulte [invocando a transformação de texto em uma extensão do vs](../modeling/invoking-text-transformation-in-a-vs-extension.md). Em outros contextos, você pode usar o mecanismo de modelagem de texto. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Use a \<#@parameter#> diretiva para passar parâmetros para esses modelos. Para obter mais informações, consulte [diretiva de parâmetro T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Ler outro arquivo de projeto de um modelo
 Para ler um arquivo do mesmo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeto que o modelo:

- Insira `hostSpecific="true"` na diretiva `<#@template#>`.

     Em seu código, use `this.Host.ResolvePath(filename)` para obter o caminho completo do arquivo.

### <a name="invoke-methods-from-a-template"></a>Invocar métodos de um modelo
 Se os métodos já existirem, por exemplo, em [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] classes padrão:

- Use a \<#@assembly#> diretiva para carregar o assembly e use \<#@import#> para definir o contexto do namespace. Para obter mais informações, consulte [diretiva de importação T4](../modeling/t4-import-directive.md).

   Se você usar frequentemente o mesmo conjunto de diretivas de assembly e importação, considere escrever um processador de diretivas. Em cada modelo, você pode invocar o processador de diretiva, que pode carregar os assemblies e os arquivos de modelo e definir o contexto do namespace. Para obter mais informações, consulte [criando processadores de diretiva de modelo de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md).

  Se você estiver escrevendo os métodos por conta própria:

- Se você estiver escrevendo um modelo de texto de tempo de execução, escreva uma definição de classe parcial que tenha o mesmo nome que o seu modelo de texto de tempo de execução. Adicione os métodos adicionais nessa classe.

- Escreva um bloco de controle de recurso `<#+ ... #>` de classe no qual você possa declarar métodos, propriedades e classes privadas. Quando o modelo de texto é compilado, ele é transformado em uma classe. Os blocos de controle padrão `<#...#>` e o texto são transformados em um único método, e os blocos de recursos de classe são inseridos como membros separados. Para obter mais informações, consulte [blocos de controle de modelo de texto](../modeling/text-template-control-blocks.md).

   Os métodos definidos como recursos de classe também podem incluir blocos de texto incorporados.

   Considere colocar recursos de classe em um arquivo separado que você possa `<#@include#>` em um ou mais arquivos de modelo.

- Escreva os métodos em um assembly separado (biblioteca de classes) e chame-os do seu modelo. Use a `<#@assembly#>` diretiva para carregar o assembly e `<#@import#>` para definir o contexto do namespace. Observe que, para recompilar o assembly enquanto você o estiver Depurando, talvez seja necessário parar e reiniciar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Para obter mais informações, consulte [diretivas de modelo de texto T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Gerar muitos arquivos de um esquema de modelo
 Se você geralmente gera arquivos de modelos que têm o mesmo esquema XML ou de banco de dados:

- Considere escrever um processador de diretriz. Isso permite que você substitua várias instruções de assembly e importe instruções em cada modelo com uma única diretiva personalizada. O processador de diretivas também pode carregar e analisar o arquivo de modelo. Para obter mais informações, consulte [criando processadores de diretiva de modelo de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Gerar arquivos de um modelo complexo

- Considere a criação de uma DSL (linguagem específica de domínio) para representar o modelo. Isso torna muito mais fácil escrever os modelos, porque você usa tipos e propriedades que refletem os nomes dos elementos em seu modelo. Você não precisa analisar o arquivo nem navegar em nós XML. Por exemplo:

     `foreach (Book book in this.Library) { ... }`

     Para obter mais informações, consulte [introdução com linguagens específicas de domínio](../modeling/getting-started-with-domain-specific-languages.md) e [gerando código de uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md).

- Considere a geração de código de um modelo UML. O código não precisa refletir o UML diretamente. Por exemplo, você não precisa gerar uma classe para cada classe no modelo UML. Em vez disso, você pode usar o diagrama de classes UML para representar um site e gerar uma página da Web de cada classe UML. Escolha o tipo de diagrama mais próximo de suas necessidades. Por exemplo, escolha diagramas de atividade para representar qualquer tipo de fluxo de trabalho. Você pode definir estereótipos para adicionar informações apropriadas ao seu aplicativo a cada tipo de elemento.

     A geração de um modelo UML permite que você desenhe e edite o modelo em um formulário diagramáticas, mas sem precisar criar seu próprio tipo de diagrama, como faria com uma DSL.

     Para obter mais informações, consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md) e [gerar arquivos de um modelo UML](../modeling/generate-files-from-a-uml-model.md).

### <a name="get-data-from-vsprvs"></a>Obter dados de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 Para usar os serviços fornecidos no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , defina o `hostSpecific` atributo e carregue o `EnvDTE` assembly. Por exemplo:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>

```

### <a name="execute-text-templates-in-the-build-process"></a>Executar modelos de texto no processo de compilação

- Para obter mais informações, consulte [geração de código em um processo de compilação](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Perguntas mais gerais

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Qual é a melhor maneira de começar a escrever um modelo de texto?

1. Escreva um exemplo específico do arquivo gerado.

2. Transforme-o em um modelo de texto inserindo a `<#@template #>` diretiva e as diretivas e o código necessários para carregar o arquivo ou modelo de entrada.

3. Substitua progressivamente partes do arquivo por blocos de expressão e de código.

### <a name="what-is-a-model"></a>O que é um “modelo”?

- A entrada lida por seu modelo. Ele pode estar em um arquivo ou em um banco de dados. Ele pode ser XML ou um desenho do Visio, ou uma DSL (linguagem específica de domínio) ou um modelo UML, ou pode ser texto sem formatação. Ele pode ser distribuído entre vários arquivos. Normalmente, mais de um modelo lê um modelo.

     A implicação do termo "modelo" é que ele representa um aspecto da sua empresa mais diretamente do que o código de programa gerado ou outros arquivos. Por exemplo, ele pode representar o plano de uma rede de comunicações que o software gerado irá supervisionar.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Qual é o benefício de usar modelos de texto?
 Normalmente, você gera vários códigos ou outros arquivos de um modelo. O modelo representa os requisitos mais diretamente do que o código gerado. Ele omite detalhes de implementação e é escrito em termos dos requisitos, em vez do código. Quando os requisitos mudam, como normalmente fazem, você pode atualizar o modelo de forma mais fácil e confiável do que as diferentes partes do código do programa.

 A geração de código é, portanto, uma ferramenta valiosa da perspectiva dos métodos de desenvolvimento Agile.

### <a name="what-best-practices-are-there-for-text-templates"></a>Quais são as "práticas recomendadas" para modelos de texto?

- Para obter mais informações, consulte [diretrizes para escrever modelos de texto T4](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>O que é "T4"?

- Outro nome para os [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] recursos de modelo de texto descritos aqui. A versão anterior, que não foi publicada, foi uma abreviação de "transformação do modelo de texto".
