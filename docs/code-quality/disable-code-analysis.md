---
title: Desativar a análise de código
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431391"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Como desativar a análise de código-fonte para código gerenciado

::: moniker range=">=vs-2019"

Esta página ajuda você a desativar a análise de código no Visual Studio. Existem limitações para o que você pode desativar, e o procedimento para desativar a análise de código difere dependendo de alguns fatores:

- Tipo de projeto (.NET Core/Standard versus .NET Framework)

  Os projetos .NET Core e .NET Standard têm opções na página de propriedades de análise de código que permitem desativar a análise de código de analisadores instalados como um pacote NuGet. Para obter mais informações, consulte [os projetos .NET Core e .NET Standard](#net-core-and-net-standard-projects). Para desativar a análise de código-fonte para projetos do .NET Framework, consulte [projetos .NET Framework](#net-framework-projects).

- Análise de origem versus análise de legado

  Este tópico se aplica à análise de código fonte e não à análise legado (binário). Para obter informações sobre como desativar a análise do legado, consulte [Como: Ativar e desativar a análise de código legado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Projetos .NET Core e .NET Standard

A partir da versão 16.3 do Visual Studio 2019, existem duas caixas de seleção disponíveis na página de propriedades de Análise de Código que permitem controlar se os analisadores são executados na hora da compilação e no tempo de design. Essas opções são específicas do projeto.

![Habilite ou desative a análise de código ao vivo ou a construção no Visual Studio](media/run-on-build-run-live-analysis.png)

Para abrir esta página, clique com o botão direito do mouse no nó do projeto no **Solution Explorer** e selecione **Propriedades**. Selecione a guia Análise de **Código.**

- Para desativar a análise de origem no momento da compilação, desfaça a opção **Executar na compilação.**
- Para desativar a análise de origem ao vivo, desfaça a opção **Executar na análise ao vivo.**

> [!NOTE]
> A partir da versão 16.5 do Visual Studio 2019, se preferir o fluxo de trabalho de execução de execução de análise de código demanda, você pode desativar a execução do analisador durante a análise ao vivo e/ou construir e acionar manualmente a análise de código uma vez em um projeto ou uma solução demanda. Para obter informações sobre como executar a análise de código manualmente, consulte [Como: Executar a análise de código manualmente para código gerenciado](how-to-run-code-analysis-manually-for-managed-code.md).  

## <a name="net-framework-projects"></a>Projetos do Quadro .NET

Para desativar a análise de código-fonte para analisadores, adicione uma ou mais das seguintes propriedades mSBuild ao arquivo do [projeto](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| Propriedade MSBuild | Descrição | Padrão |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controla se os analisadores são executados no tempo de construção. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controla se os analisadores analisam o código ao vivo na hora do projeto. | `true` |
| `RunAnalyzers` | Desativa os analisadores tanto no tempo de construção quanto no design. Esta propriedade tem `RunAnalyzersDuringBuild` precedência sobre e `RunAnalyzersDuringLiveAnalysis`. | `true` |

Exemplos:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Análise de código-fonte

Não é possível desativar a [análise de origem](roslyn-analyzers-overview.md) no Visual Studio 2017. Se você quiser limpar erros do analisador da Lista de erros, você pode suprimir todas as violações atuais, escolhendo Analisar análise de código de **execução** > **e suprimir problemas ativos** na barra de menu. Para obter mais informações, consulte [Suprimir violações](use-roslyn-analyzers.md#suppress-violations).

A partir da versão 16.3 do Visual Studio 2019, você pode desativar a análise do código fonte ou executá-la demanda. Considere atualizar para o Visual Studio 2019.

## <a name="legacy-analysis"></a>Análise herdada

Você pode desativar a análise de tempo de construção legado na página de propriedades de análise de **código.** Para obter mais informações, [consulte Como: Ativar e desativar a análise de código legado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Confira também

- [Suprimir violações](use-roslyn-analyzers.md#suppress-violations)
- [Como: Ativar e desativar a análise de código legado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
