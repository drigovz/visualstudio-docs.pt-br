---
title: EditorConfig versus analisadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b0c0defe5593c9dc0e2111ef5984a5c51eaf55
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760137"
---
# <a name="code-analysis-faq"></a>Perguntas frequentes sobre análise de código

Esta página contém respostas a algumas perguntas frequentes sobre a análise de código baseada em plataforma do .NET Compiler no Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análise de código versus EditorConfig

**P:** Devo usar a análise de código ou o EditorConfig para verificar o estilo de código?

**A:** Análise de código e arquivos EditorConfig funcionam lado a lado. Quando você define estilos de código [em um arquivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ou na página Opções do [editor de texto,](../ide/code-styles-and-code-cleanup.md) você está realmente configurando os analisadores de código que são incorporados no Visual Studio. Os arquivos EditorConfig podem ser usados para ativar ou desativar as regras do analisador, e também para configurar alguns pacotes de analisadores NuGet, como [analisadores FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig versus conjuntos de regras

**P:** Devo configurar meus analisadores usando um conjunto de regras ou um arquivo EditorConfig?

**A**: Conjuntos de regras e arquivos EditorConfig podem coexistir e podem ser usados para configurar analisadores. Ambos os arquivos do EditorConfig e conjuntos de regras permitem que você habilite e desative regras e defina sua gravidade.

No entanto, os arquivos EditorConfig oferecem maneiras adicionais de configurar regras também:

- Para analisadores FxCop, os arquivos EditorConfig permitem [definir quais tipos de código analisar](fxcop-analyzer-options.md).
- Para os analisadores de estilo de código que são incorporados ao Visual Studio, os arquivos EditorConfig permitem [definir os estilos de código preferidos](../ide/editorconfig-code-style-settings-reference.md) para uma base de código.

Além de conjuntos de regras e arquivos EditorConfig, alguns analisadores são configurados através do uso de arquivos de texto marcados como [arquivos adicionais](../ide/build-actions.md#build-action-values) para os compiladores C# e VB.

> [!NOTE]
> - Os arquivos EditorConfig só podem ser usados para habilitar regras e definir sua gravidade na versão 16.3 do Visual Studio 2019 e posterior.
> - Os arquivos EditorConfig não podem ser usados para configurar a análise de legado, enquanto os conjuntos de regras podem.

## <a name="code-analysis-in-ci-builds"></a>Análise de código em construções de CI

**P:** A análise de código baseada em plataforma do .NET Compiler funciona em compilações de integração contínua (CI) ?

**A:** Sim. Para analisadores instalados a partir de um pacote NuGet, essas regras são [aplicadas no tempo de compilação,](roslyn-analyzers-overview.md#build-errors)inclusive durante uma compilação de CI. Os analisadores usados em CI respeitam a configuração de regras de ambos os conjuntos de regras e arquivos EditorConfig. Atualmente, os analisadores de código que são incorporados ao Visual Studio não estão disponíveis como um pacote NuGet e, portanto, essas regras não são aplicáveis em uma compilação de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analisadores IDE versus StyleCop

**P**: Qual é a diferença entre os analisadores de código Visual Studio IDE e os analisadores StyleCop?

**R:** O Visual Studio IDE inclui analisadores embutidos que buscam tanto o estilo de código quanto os problemas de qualidade. Essas regras ajudam você a usar novos recursos de linguagem à medida que são introduzidos e melhoram a manutenção do seu código. Os analisadores IDE são continuamente atualizados a cada lançamento do Visual Studio.

[Os analisadores StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) são analisadores de terceiros instalados como um pacote NuGet que verifica a consistência do estilo em seu código. Em geral, as regras do StyleCop permitem definir preferências pessoais para uma base de código sem recomendar um estilo em vez de outro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analisadores de código versus análise de legado

**P**: Qual é a diferença entre análise de legado e análise de código baseada em plataforma .NET Compiler?

**A:**.NET Compiler A análise de código baseada em plataforma analisa o código-fonte em tempo real e durante a compilação, enquanto a análise herdada analisa arquivos binários após a compilação ter sido concluída. Para obter mais informações, consulte [análise baseada em plataforma do .NET Compiler versus análise de legado](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) e perguntas [frequentes sobre análise supresso.](fxcop-analyzers-faq.md)

## <a name="treat-warnings-as-errors"></a>Tratar avisos como erros

**P**: Meu projeto usa a opção de compilação para tratar avisos como erros. Depois de migrar da análise do legado para a análise do código fonte, todos os avisos de análise de código estão agora aparecendo como erros. Como posso evitar isso?

**A:** Para evitar que os avisos de análise de código sejam tratados como erros, siga estas etapas:

  1. Criar um arquivo .props com o seguinte conteúdo:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Adicione uma linha ao seu arquivo de projeto .csproj ou .vbproj para importar o arquivo .props que você criou na etapa anterior. Esta linha deve ser colocada antes de qualquer linha que importe os arquivos .props do analisador FxCop. Por exemplo, se o arquivo .props for chamado codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Página de propriedade da solução de análise de código

**P:** Onde está a página de propriedade de Análise de Código para a solução?

**R:** A página de propriedade de Análise de Código no nível da solução foi removida em favor do grupo de propriedade compartilhada mais confiável. Para gerenciar a Análise de Código no nível do projeto, a página de propriedade De Análise de Código ainda está disponível. (Para projetos gerenciados, também recomendamos migrar de conjuntos de regras para EditorConfig para configuração de regras.)  Para compartilhar conjuntos de regras em vários/todos os projetos em uma solução ou um repo, recomendamos definir um grupo de propriedades com a propriedade CodeAnalysisRuleSet em um arquivo de adereços/alvos compartilhados ou o arquivo Directory.props/Directory.targets. Se você não tiver tais adereços ou metas comuns que todos os seus projetos importam, você deve considerar [adicionar tal grupo de propriedade a um Diretório.props ou a um diretório.targets em um diretório de soluções de alto nível, que é automaticamente importado em todos os arquivos de projeto definidos no diretório ou em seus subdiretórios](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets).

## <a name="see-also"></a>Confira também

- [Visão geral dos analisadores](roslyn-analyzers-overview.md)
- [Configurações de convenção de codificação .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
