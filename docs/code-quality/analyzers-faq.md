---
title: EditorConfig versus analisadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdc30d0299e83423474c673b9d32e019885c2d52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603885"
---
# <a name="code-analysis-faq"></a>Perguntas frequentes sobre análise de código

Esta página contém respostas para algumas perguntas frequentes sobre a análise de código baseada em .NET Compiler Platform no Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análise de código versus EditorConfig

**P**: devo usar a análise de código ou EditorConfig para verificar o estilo de código?

**R: A**análise de código e os arquivos EditorConfig funcionam lado a lado. Quando você define estilos [de código em um arquivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ou na página de [Opções do editor de texto](../ide/code-styles-and-code-cleanup.md) , na verdade está configurando os analisadores de código que são criados no Visual Studio. Os arquivos EditorConfig podem ser usados para habilitar ou desabilitar as regras do analisador e também para configurar alguns pacotes do analisador NuGet, como [analisadores do FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig versus conjuntos de regras

**P**: devo configurar meus analisadores usando um conjunto de regras ou um arquivo EditorConfig?

**R**: conjuntos de regras e arquivos EditorConfig podem coexistir e ambos podem ser usados para configurar analisadores. Os arquivos EditorConfig e os conjuntos de regras permitem habilitar e desabilitar regras e definir sua gravidade.

No entanto, os arquivos EditorConfig oferecem maneiras adicionais de configurar regras também:

- Para analisadores do FxCop, os arquivos EditorConfig permitem que você [Defina quais tipos de código analisar](fxcop-analyzer-options.md).
- Para analisadores de estilo de código que são criados no Visual Studio, os arquivos EditorConfig permitem que você [defina os estilos de código preferenciais](../ide/editorconfig-code-style-settings-reference.md) para uma codebase.

Além dos conjuntos de regras e arquivos EditorConfig, alguns analisadores são configurados por meio do uso de arquivos de texto marcados como C# [arquivos adicionais](../ide/build-actions.md#build-action-values) para os compiladores do e do VB.

> [!NOTE]
> - Os arquivos EditorConfig só podem ser usados para habilitar regras e definir sua gravidade no Visual Studio 2019 versão 16,3 e posterior.
> - Os arquivos EditorConfig não podem ser usados para configurar a análise herdada, enquanto os conjuntos de regras podem.

## <a name="code-analysis-in-ci-builds"></a>Análise de código em compilações CI

**P**: a análise de código baseada em .net Compiler Platform funciona em compilações de CI (integração contínua)?

**R**: Sim. Para analisadores que são instalados a partir de um pacote NuGet, essas regras são [impostas no momento da compilação](roslyn-analyzers-overview.md#build-errors), incluindo durante uma compilação de CI. Os analisadores usados em compilações de CI respeitam a configuração de regra dos conjuntos de regras e dos arquivos EditorConfig. Atualmente, os analisadores de código que são criados no Visual Studio não estão disponíveis como um pacote NuGet e, portanto, essas regras não são impostas em uma compilação de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analisadores IDE versus StyleCop

**P**: Qual é a diferença entre os analisadores de código do IDE do Visual Studio e os analisadores do StyleCop?

**R**: o IDE do Visual Studio inclui analisadores internos que procuram problemas de qualidade e estilo de código. Essas regras ajudam você a usar novos recursos de linguagem à medida que são introduzidos e aprimoram a manutenção do seu código. Os analisadores IDE são continuamente atualizados com cada versão do Visual Studio.

[Analisadores de StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) são analisadores de terceiros instalados como um pacote NuGet que verifica a consistência de estilo em seu código. Em geral, as regras de StyleCop permitem definir preferências pessoais para uma base de código sem recomendar um estilo em vez de outra.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analisadores de código versus análise herdada

**P**: Qual é a diferença entre análise herdada e análise de código baseada em .net Compiler Platform?

**R**: a análise de código baseada em .net Compiler Platform analisa o código-fonte em tempo real e durante a compilação, enquanto a análise herdada analisa arquivos binários após a conclusão da compilação. Para obter mais informações, consulte [análise baseada em .net Compiler Platform em comparação com](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) as [perguntas frequentes sobre](fxcop-analyzers-faq.md)análise de herança e analisadores de FxCop.

## <a name="treat-warnings-as-errors"></a>Tratar avisos como erros

**P**: meu projeto usa a opção de compilação para tratar avisos como erros. Depois de migrar da análise herdada para a análise de código-fonte, todos os avisos de análise de código agora aparecem como erros. Como posso evitar isso?

**R**: para impedir que avisos de análise de código sejam tratados como erros, siga estas etapas:

  1. Crie um arquivo. props com o seguinte conteúdo:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Adicione uma linha a seu arquivo de projeto. csproj ou. vbproj para importar o arquivo. props criado na etapa anterior. Essa linha deve ser colocada antes de qualquer linha que importe os arquivos do FxCop Analyzer. props. Por exemplo, se o arquivo. props for nomeado CodeAnalysis. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores](roslyn-analyzers-overview.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
