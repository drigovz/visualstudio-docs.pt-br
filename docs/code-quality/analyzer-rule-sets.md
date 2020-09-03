---
title: Conjuntos de regras e arquivos editorconfig do FxCop Analyzer
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b99bb08c82725f19f7985a97656edf65f112d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800210"
---
# <a name="enable-a-category-of-rules"></a>Habilitar uma categoria de regras

Os pacotes do Analyzer podem incluir [EditorConfig](use-roslyn-analyzers.md#rule-severity) predefinidos e arquivos de [conjunto de regras](using-rule-sets-to-group-code-analysis-rules.md) que tornam rápido e fácil habilitar uma categoria de regras, como segurança ou regras de design. O pacote do [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer inclui os dois conjuntos de regras (começando na versão 2.6.2) e os arquivos EditorConfig (a partir da versão 2.9.5). Ao habilitar uma categoria específica de regras, você pode identificar problemas direcionados e condições específicas.

> [!NOTE]
> A habilitação das regras do analisador e a definição de sua gravidade usando um arquivo EditorConfig tem suporte a partir do Visual Studio 2019 versão 16,3.

O pacote NuGet Analyzer do FxCop inclui conjuntos de regras predefinidos e arquivos EditorConfig para as seguintes categorias de regra:

- Todas as regras
- Fluxo de dados
- Design
- Documentação
- Globalização
- Interoperabilidade
- Facilidade de manutenção
- Nomenclatura
- Desempenho
- Portado do FxCop
- Confiabilidade
- Segurança
- Uso

Cada uma dessas categorias de regras tem um EditorConfig ou um arquivo de conjunto de regras para:

- Habilitar todas as regras na categoria (e desabilitar todas as outras regras)
- usar a configuração de gravidade e a habilitação padrão de cada regra (e desabilitar todas as outras regras)

> [!TIP]
> A categoria "todas as regras" tem um EditorConfig adicional ou um arquivo de conjunto de regras para desabilitar todas as regras. Use esse arquivo para eliminar rapidamente qualquer erro ou aviso do analisador em um projeto.

> [!TIP]
> Se você estiver migrando da análise "FxCop" herdada para a análise de código baseada em .NET Compiler Platform, os arquivos de conjunto de regras e EditorConfig permitem que você continue usando configurações de regra semelhantes [àquelas usadas anteriormente](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Arquivos EditorConfig predefinidos

Os arquivos EditorConfig predefinidos para o pacote do analisador Microsoft. CodeAnalysis. FxCopAnalyzers estão localizados no diretório *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \editorconfig* . Por exemplo, o arquivo EditorConfig para habilitar todas as regras de segurança está localizado em *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Copie o arquivo. editorconfig escolhido para o diretório raiz do projeto.

## <a name="predefined-rule-sets"></a>Conjuntos de regras predefinidas

Os arquivos de conjunto de regras predefinidos para o pacote do analisador Microsoft. CodeAnalysis. FxCopAnalyzers estão localizados no diretório *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \rulesets* . Por exemplo, o arquivo de conjunto de regras para habilitar todas as regras de segurança está localizado em *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.RuleSet*.

Copie um ou mais conjuntos de regras e cole-os no diretório que contém o projeto do Visual Studio ou diretamente no **Gerenciador de soluções**.

Você também pode [Personalizar um conjunto de regras predefinidas](how-to-create-a-custom-rule-set.md) para sua preferência. Por exemplo, você pode alterar a severidade de uma ou mais regras para que as violações apareçam como erros ou avisos no **lista de erros**.

### <a name="set-the-active-rule-set"></a>Definir o conjunto de regras ativas

O processo de configuração do conjunto de regras ativo é um pouco diferente, dependendo se você tem um projeto padrão .NET Core/. NET ou um projeto .NET Framework.

#### <a name="net-core"></a>.NET Core

Para fazer com que uma regra defina o conjunto de regras ativas para análise no .NET Core ou .NET Standard projetos, adicione manualmente a propriedade **CodeAnalysisRuleSet** ao seu arquivo de projeto. Por exemplo, o trecho de código a seguir define `HelloWorld.ruleset` como o conjunto de regras ativas.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

Para fazer com que uma regra defina o conjunto de regras ativas para análise em projetos .NET Framework:

- Clique com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecione **Propriedades**.

- Nas páginas de propriedades do projeto, selecione a guia **análise de código** .

::: moniker range="vs-2017"

- Em **executar este conjunto de regras**, selecione **procurar**e escolha o conjunto de regras desejado que você copiou para o diretório do projeto.

::: moniker-end

::: moniker range=">=vs-2019"

- Em **regras ativas**, selecione **procurar**e escolha o conjunto de regras desejado que você copiou para o diretório do projeto.

::: moniker-end

   Agora você só vê violações de regra para as regras que estão habilitadas no conjunto de regras selecionado.

## <a name="see-also"></a>Confira também

- [Perguntas frequentes sobre analisadores](analyzers-faq.md)
- [Visão geral dos analisadores do .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Instalar analisadores](install-roslyn-analyzers.md)
- [Configurar analisadores](use-roslyn-analyzers.md)
- [Usar conjuntos de regras para agrupar regras de análise de código](using-rule-sets-to-group-code-analysis-rules.md)
