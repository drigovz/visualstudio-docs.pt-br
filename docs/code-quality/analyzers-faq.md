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
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57874651"
---
# <a name="analyzers-faq"></a>Analisadores de perguntas Frequentes

Esta página contém respostas para algumas perguntas frequentes sobre os analisadores de Roslyn no Visual Studio.

## <a name="roslyn-analyzers-versus-editorconfig"></a>Roslyn analyzers versus .editorconfig

**Q**: Deve usar os analisadores de Roslyn ou. editorconfig para o estilo de código?

**R**: Analisadores de Roslyn e arquivos. editorconfig funcionam em mãos. Ao definir estilos de código [em um arquivo. editorconfig](../ide/editorconfig-code-style-settings-reference.md) ou o [editor de texto opções](../ide/code-styles-and-quick-actions.md) página, na verdade, você está configurando os analisadores do Roslyn que são criados no Visual Studio. Arquivos de EditorConfig também podem ser usados para configurar alguns pacotes do analisador de terceiros, como [analisadores FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig versus conjuntos de regras

**Q**: Devo configurar meu analisadores usando um conjunto de regras ou um arquivo. editorconfig?

**R**: Conjuntos de regras e arquivos. editorconfig são mutuamente exclusivas maneiras de configurar os analisadores. Eles podem coexistir. [Conjuntos de regra](analyzer-rule-sets.md) permitem que você habilitar e desabilitar regras e definir sua gravidade. Arquivos de EditorConfig oferecem outras maneiras de configurar as regras. Para os analisadores FxCop, arquivos. editorconfig permitem [definem quais tipos de código para analisar](fxcop-analyzer-options.md). Para os analisadores que são criados no Visual Studio, arquivos. editorconfig permitem [definir os estilos de código preferido](../ide/editorconfig-code-style-settings-reference.md) para uma base de código.

Além dos conjuntos de regras e arquivos. editorconfig, alguns analisadores de terceiros são configurados com o uso de arquivos de texto marcados como [arquivos adicionais](../ide/build-actions.md#build-action-values) para o C# e compiladores VB.

> [!NOTE]
> Arquivos EditorConfig não podem ser usados para configurar regras de análise de código estático, enquanto os conjuntos de regras podem.

## <a name="analyzers-in-ci-builds"></a>Analisadores em builds de CI

**Q**: Analisadores funcionam em builds de CI (integração contínua)?

**R**: Sim. Os analisadores que são instalados a partir de um pacote do NuGet, essas regras estão [imposto no momento da compilação](roslyn-analyzers-overview.md#build-errors), incluindo durante um build de CI. Analisadores usados na configuração de regra de respeito de compilações de CI para ambos [conjuntos de regras](analyzer-rule-sets.md) e [arquivos. editorconfig](configure-fxcop-analyzers.md). Atualmente, os analisadores de código que são criados no Visual Studio não estão disponíveis como um pacote do NuGet, e portanto, essas regras não são aplicáveis em uma compilação de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analisadores IDE versus o StyleCop

**Q**: O que é a diferença entre o StyleCop analisadores e analisadores de código do Visual Studio IDE?

**R**: O IDE do Visual Studio inclui os analisadores internos que procuram os dois problemas de estilo e a qualidade do código. Essas regras ajudarão a usar os novos recursos de linguagem conforme eles são introduzidos e melhorar a facilidade de manutenção do seu código. Analisadores IDE são continuamente atualizados a cada versão do Visual Studio.

[Os analisadores do StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) são analisadores de terceiros instalados como um pacote do NuGet que verificar a consistência de estilo no seu código. Em geral, as regras do StyleCop permitem que você defina preferências pessoais para um código base sem recomendar um estilo em detrimento de outro.

## <a name="analyzers-versus-static-code-analysis"></a>Analisadores versus a análise de código estático

**Q**: O que é a diferença entre os analisadores e análise de código estático?

**R**: Analisadores de analisar o código-fonte em tempo real e durante a compilação, enquanto a análise de código estático analisa os arquivos binários após a conclusão da compilação. Para obter mais informações, consulte [analisadores de Roslyn versus a análise de código estático](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis) e [analisadores FxCop perguntas frequentes sobre](fxcop-analyzers-faq.md).

## <a name="see-also"></a>Consulte também

- [Visão geral de analisadores](roslyn-analyzers-overview.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)