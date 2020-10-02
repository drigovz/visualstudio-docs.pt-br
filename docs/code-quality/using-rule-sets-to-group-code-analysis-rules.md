---
title: Conjunto de regras da análise de código
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47019ecd01a4ad432a853a7f1a4f7d7112be163c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659199"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Usar conjuntos de regras para agrupar regras de análise de código

Ao configurar a análise de código no Visual Studio, você pode escolher em uma lista de conjuntos de *regras*internos. Um conjunto de regras é um agrupamento de regras de análise de código que identificam problemas direcionados e condições específicas para esse projeto. Por exemplo, você pode aplicar um conjunto de regras que foi projetado para verificar o código para APIs disponíveis publicamente. Você também pode aplicar um conjunto de regras que inclui todas as regras disponíveis.

Você pode personalizar um conjunto de regras adicionando ou excluindo regras ou alterando severidades de regra para que apareçam como avisos ou erros no **lista de erros**. Conjuntos de regras personalizados podem atender a uma necessidade de seu ambiente de desenvolvimento específico. Quando você personaliza um conjunto de regras, o editor de conjunto de regras fornece ferramentas de pesquisa e filtragem para ajudá-lo no processo.

Os conjuntos de regras estão disponíveis para [análise de código gerenciado](/dotnet/fundamentals/code-analysis/code-quality-rule-options), [análise herdada de código gerenciado](how-to-configure-code-analysis-for-a-managed-code-project.md)e [análise de código C++](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

## <a name="rule-set-format"></a>Formato do conjunto de regras

Um conjunto de regras é especificado no formato XML em um arquivo *. RuleSet* . As regras, que consistem em uma ID e uma *ação*, são agrupadas por ID do analisador e namespace no arquivo.

O conteúdo de um arquivo *. RuleSet* é semelhante a este XML:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> É mais fácil [Editar um conjunto de regras](../code-quality/working-in-the-code-analysis-rule-set-editor.md) no editor de **conjunto de regras** gráficas do que manualmente.

## <a name="specify-a-rule-set-for-a-project"></a>Especificar um conjunto de regras para um projeto

O conjunto de regras para um projeto é especificado pela propriedade **CodeAnalysisRuleSet** no arquivo de projeto do Visual Studio. Por exemplo:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Confira também

- [Referência do conjunto de regras da análise de código](../code-quality/rule-set-reference.md)
