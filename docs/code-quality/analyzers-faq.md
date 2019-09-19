---
title: EditorConfig versus analisadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26e48664c40db018df60f2b6d600fab0767a7b72
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062174"
---
# <a name="code-analysis-faq"></a>Perguntas frequentes sobre análise de código

Esta página contém respostas para algumas perguntas frequentes sobre a análise de código baseada em .NET Compiler Platform no Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análise de código versus EditorConfig

**P**: Devo usar a análise de código ou EditorConfig para verificar o estilo de código?

**R**: A análise de código e os arquivos EditorConfig funcionam lado a lado. Quando você define estilos [de código em um arquivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ou na página de [Opções do editor de texto](../ide/code-styles-and-code-cleanup.md) , na verdade está configurando os analisadores de código que são criados no Visual Studio. Os arquivos EditorConfig também podem ser usados para configurar alguns pacotes do NuGet Analyzer, como [analisadores do FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig versus conjuntos de regras

**P**: Devo configurar meus analisadores usando um conjunto de regras ou um arquivo EditorConfig?

**R**: Os conjuntos de regras e os arquivos EditorConfig podem coexistir e podem ser usados para configurar analisadores. Os [conjuntos de regras](analyzer-rule-sets.md) permitem habilitar e desabilitar regras e definir sua gravidade. Os arquivos EditorConfig oferecem outras maneiras de configurar regras. Para analisadores do FxCop, os arquivos EditorConfig permitem que você [Defina quais tipos de código analisar](fxcop-analyzer-options.md). Para analisadores de estilo de código que são criados no Visual Studio, os arquivos EditorConfig permitem que você [defina os estilos de código preferenciais](../ide/editorconfig-code-style-settings-reference.md) para uma codebase.

Além dos conjuntos de regras e arquivos EditorConfig, alguns analisadores são configurados por meio do uso de arquivos de texto marcados como C# [arquivos adicionais](../ide/build-actions.md#build-action-values) para os compiladores do e do VB.

> [!NOTE]
> Os arquivos EditorConfig não podem ser usados para configurar a análise herdada, enquanto os conjuntos de regras podem.

## <a name="code-analysis-in-ci-builds"></a>Análise de código em compilações CI

**P**: A análise de código baseada em .NET Compiler Platform funciona em compilações de CI (integração contínua)?

**R**: Sim. Para analisadores que são instalados a partir de um pacote NuGet, essas regras são [impostas no momento da compilação](roslyn-analyzers-overview.md#build-errors), incluindo durante uma compilação de CI. Os analisadores usados em compilações de CI respeitam a configuração de regra de ambos os [conjuntos de regras](analyzer-rule-sets.md) e [arquivos. editorconfig](configure-fxcop-analyzers.md). Atualmente, os analisadores de código que são criados no Visual Studio não estão disponíveis como um pacote NuGet e, portanto, essas regras não são impostas em uma compilação de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analisadores IDE versus StyleCop

**P**: Qual é a diferença entre os analisadores de código do IDE do Visual Studio e os analisadores do StyleCop?

**R**: O IDE do Visual Studio inclui analisadores internos que procuram problemas de qualidade e estilo de código. Essas regras ajudam você a usar novos recursos de linguagem à medida que são introduzidos e aprimoram a manutenção do seu código. Os analisadores IDE são continuamente atualizados com cada versão do Visual Studio.

[Analisadores de StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) são analisadores de terceiros instalados como um pacote NuGet que verifica a consistência de estilo em seu código. Em geral, as regras de StyleCop permitem definir preferências pessoais para uma base de código sem recomendar um estilo em vez de outra.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analisadores de código versus análise herdada

**P**: Qual é a diferença entre análise herdada e análise de código baseada em .NET Compiler Platform?

**R**: a análise de código baseada em .net Compiler Platform analisa o código-fonte em tempo real e durante a compilação, enquanto a análise herdada analisa arquivos binários após a conclusão da compilação. Para obter mais informações, consulte [análise baseada em .net Compiler Platform em comparação com](roslyn-analyzers-overview.md#net-compiler-platform-based-analysis-versus-legacy-analysis) as [perguntas frequentes sobre](fxcop-analyzers-faq.md)análise de herança e analisadores de FxCop.

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores](roslyn-analyzers-overview.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
