---
title: Conjuntos de regras do analisador
ms.date: 07/20/2018
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da5eab1424ac6f6fe580ec0f71ec3efd6e120020
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57866991"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Conjuntos de regras para analisadores de Roslyn

Conjuntos de regras predefinidas são incluídos com alguns pacotes NuGet do analisador. Por exemplo, os conjuntos de regras que são incluídos com o [fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pacote do NuGet analyzer (começando na versão 2.6.2) habilitar ou desabilitar regras com base em sua categoria, como segurança, nomenclatura, ou desempenho. Usando conjuntos de regras torna mais fácil ver rapidamente apenas essas violações de regra que pertencem a uma determinada categoria de regra.

Se você estiver migrando de análise de código estático "FxCop" herdada para analisadores de Roslyn, esses conjuntos de regras permitem que você continue usando as mesmas configurações de regra que você usou anteriormente.

## <a name="use-analyzer-rule-sets"></a>Usar conjuntos de regras do analisador

Depois que você [instalar um pacote do NuGet analyzer](install-roslyn-analyzers.md), localize a conjunto de regras predefinidas seus *rulesets* diretório, por exemplo *% USERPROFILE %\\.nuget\packages\ Microsoft.codequality.Analyzers\<versão > \rulesets*. A partir daí, você pode arrastar e soltar, ou copiar e colar, um ou mais dos conjuntos de regras ao seu projeto do Visual Studio no **Gerenciador de soluções**.

Para tornar uma regra para definir a regra ativa definido para análise, clique com botão direito no projeto no **Gerenciador de soluções** e escolha **propriedades**. Nas páginas de propriedade do projeto, selecione a **análise de código** guia. Sob **executar este conjunto de regras**, selecione **procurar**e, em seguida, selecione o conjunto de regras desejado que você copiou para o diretório do projeto. Agora, você verá somente as violações de regra para as regras que estão habilitadas no conjunto de regras selecionado.

Você também pode [personalizar um conjunto de regras predefinidas](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set) com sua preferência. Por exemplo, você pode alterar a gravidade de uma ou mais regras para que sejam exibidos violações como erros ou avisos na **Error List**.

## <a name="available-rule-sets"></a>Conjuntos de regras disponíveis

Os conjuntos de regra do analisador predefinido incluem três conjuntos de regras que afetam todas as regras no pacote&mdash;que permite que todos eles, que desabilita todas elas e um que respeita as configurações de habilitação e a gravidade de cada da regra padrão:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Além disso, há dois conjuntos de regras para cada categoria de regras no pacote, como desempenho ou segurança. Um conjunto de regras permite que todas as regras para a categoria e um conjunto de regras respeita as configurações de severidade e habilitação de padrão para cada regra na categoria.

O [fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) pacote do NuGet do analisador inclui conjuntos de regras para as seguintes categorias, que correspondem aos conjuntos de regras disponíveis para análise de código estático "FxCop" herdados:

- design
- documentação
- facilidade de manutenção
- nomenclatura
- desempenho
- confiabilidade
- segurança
- uso

## <a name="see-also"></a>Consulte também

- [Analisadores de perguntas Frequentes](analyzers-faq.md)
- [Visão geral dos analisadores do .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Instalar analisadores](install-roslyn-analyzers.md)
- [Usar analisadores](use-roslyn-analyzers.md)
- [Usar conjuntos de regras para agrupar regras de análise de código](using-rule-sets-to-group-code-analysis-rules.md)