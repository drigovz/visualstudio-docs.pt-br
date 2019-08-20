---
title: Conjuntos de regras do Analyzer
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68410fd43f182873c27e3d5fed742bed7ba8a4ed
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585140"
---
# <a name="rule-sets-for-analyzer-packages"></a>Conjuntos de regras para pacotes do analisador

Conjuntos de regras predefinidos são incluídos em alguns pacotes do analisador NuGet. Por exemplo, os conjuntos de regras que estão incluídos no pacote do [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer (a partir da versão 2.6.2) habilitam ou desabilitam regras com base em sua categoria, como segurança, nomenclatura ou desempenho. O uso de conjuntos de regras facilita a visualização rápida apenas das violações de regra que pertencem a uma determinada categoria de regra.

Se você estiver migrando da análise "FxCop" herdada para a análise de código baseada em .NET Compiler Platform, esses conjuntos de regras permitirão que você continue usando configurações de regra semelhantes [àquelas usadas anteriormente](rule-set-reference.md).

## <a name="use-analyzer-package-rule-sets"></a>Usar conjuntos de regras de pacote do analisador

Depois de [instalar um pacote do NuGet Analyzer](install-roslyn-analyzers.md), localize o conjunto de regras predefinidas em seu diretório *RuleSets* . Por exemplo, se você referenciou o `Microsoft.CodeAnalysis.FxCopAnalyzers` pacote do analisador, poderá encontrar seu diretório RuleSets em *% USERPROFILE%\\. versão\\nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\< \rulesets\>* . A partir daí, copie um ou mais conjuntos de regras e cole-os no diretório que contém seu projeto do Visual Studio ou diretamente em **Gerenciador de soluções**.

Você também pode [Personalizar um conjunto de regras](how-to-create-a-custom-rule-set.md) predefinidas para sua preferência. Por exemplo, você pode alterar a severidade de uma ou mais regras para que as violações apareçam como erros ou avisos no **lista de erros**.

## <a name="set-the-active-rule-set"></a>Definir o conjunto de regras ativas

O processo de configuração do conjunto de regras ativo é um pouco diferente, dependendo se você tem um projeto padrão .NET Core/. NET ou um projeto .NET Framework.

### <a name="net-core"></a>.NET Core

Para fazer com que uma regra defina o conjunto de regras ativas para análise no .NET Core ou .NET Standard projetos, adicione manualmente a propriedade **CodeAnalysisRuleSet** ao seu arquivo de projeto. Por exemplo, o trecho de código a `HelloWorld.ruleset` seguir define como o conjunto de regras ativas.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Para fazer com que uma regra defina o conjunto de regras ativo para análise em projetos .NET Framework, clique com o botão direito do mouse no projeto em **Gerenciador de soluções** e escolha **Propriedades**. Nas páginas de propriedades do projeto, selecione a guia **análise de código** . Em **executar este conjunto de regras**, selecione **procurar**e, em seguida, selecione o conjunto de regras desejado que você copiou para o diretório do projeto. Agora você só vê violações de regra para as regras que estão habilitadas no conjunto de regras selecionado.

## <a name="available-rule-sets"></a>Conjuntos de regras disponíveis

Os conjuntos de regras de analisador predefinidos incluem três conjuntos de regras que afetam&mdash;todas as regras no pacote um que habilita todos eles, um que desabilita todos eles e um que respeita as configurações padrão de gravidade e habilitação de cada regra:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Além disso, há dois conjuntos de regras para cada categoria de regras no pacote, como desempenho ou segurança. Um conjunto de regras habilita todas as regras para a categoria, e um conjunto de regras respeita as configurações padrão de gravidade e habilitação de cada regra na categoria.

O pacote do [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer inclui conjuntos de regras para as seguintes categorias:

- design
- documentação
- facilidade de manutenção
- nomenclatura
- desempenho
- confiabilidade
- segurança
- uso

## <a name="see-also"></a>Consulte também

- [Perguntas frequentes sobre analisadores](analyzers-faq.md)
- [Visão geral dos analisadores do .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Instalar analisadores](install-roslyn-analyzers.md)
- [Usar analisadores](use-roslyn-analyzers.md)
- [Usar conjuntos de regras para agrupar regras de análise de código](using-rule-sets-to-group-code-analysis-rules.md)
