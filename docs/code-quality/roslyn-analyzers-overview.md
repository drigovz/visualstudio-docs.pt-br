---
title: Análise de código usando os analisadores do Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431274"
---
# <a name="overview-of-source-code-analyzers"></a>Visão geral dos analisadores de código-fonte

Os analisadores de código .NET Compiler Platform ("Roslyn") inspecionam seu código C# ou Visual Basic para obter estilo, qualidade e manutenção, design e outros problemas.

- Alguns analisadores são incorporados ao Visual Studio. O ID de diagnóstico, ou código, para esses analisadores é do formato IDExxxx, por exemplo, IDE0067. A maioria desses analisadores incorporados inspeciona o estilo de [código](../ide/code-styles-and-code-cleanup.md)e você pode configurar preferências na [página de opções](../ide/code-styles-and-code-cleanup.md) do editor de texto ou em um [arquivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Um punhado de analisadores embutidos olham para a qualidade do código.

- Você pode instalar analisadores adicionais como um pacote NuGet ou uma extensão do Visual Studio. Por exemplo: 

  - [Analisadores FXCop](../code-quality/install-fxcop-analyzers.md), analisadores de qualidade de código recomendados pela Microsoft
  - Analisadores de terceiros, como [StyleCop,](https://www.nuget.org/packages/StyleCop.Analyzers/) [Roslynator,](https://www.nuget.org/packages/Roslynator.Analyzers/) [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)e [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Se as violações de regras forem encontradas por um analisador, elas serão relatadas no editor de código (como um *squiggle* o código ofensivo) e na janela Lista de erros.

Muitas regras do analisador ou *diagnósticos* têm uma ou mais *correções de código* associadas que podem ser aplicadas para corrigir o problema. Cada diagnóstico do analisador inserido no Visual Studio tem uma correção de código associada. As correções de código são mostradas no menu do ícone de lâmpada, juntamente com outros tipos de [Ações rápidas](../ide/quick-actions.md). Para saber mais sobre essas correções de código, confira [Ações rápidas comuns](../ide/common-quick-actions.md).

![Violação do analisador e correção de código de Ação Rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Análise de código-fonte versus análise de legado

A análise de origem dos analisadores Roslyn substitui a [análise legado](../code-quality/code-analysis-for-managed-code-overview.md) por código gerenciado. Muitas das regras de análise do legado já foram reescritas como analisadores de código roslyn. Para modelos de projetos mais novos, como .NET Core e .NET Standard, a análise de legado nem está disponível.

Como violações de regras de análise de legado, violações de análise de código-fonte aparecem na janela Lista de erros no Visual Studio. Além disso, as violações da análise de código fonte também aparecem no editor de código como *squiggles* o código ofensivo. A cor da linha ondulada depende da [configuração de gravidade](../code-quality/use-roslyn-analyzers.md#rule-severity) da regra. A imagem a seguir&mdash;mostra três violações um vermelho, um verde e um cinza:

![Squiggles no editor de código no Visual Studio](media/diagnostics-severity-colors.png)

Os analisadores de código inspecionam o código no momento da compilação, como a análise de legado, se estiver habilitada, mas também vivem como você digita. Você pode configurar o escopo da análise de código vivo para executar apenas para o documento atual, todos os documentos abertos ou toda a solução. [Veja Como: Configurar o escopo da análise de código ao vivo.](./configure-live-code-analysis-scope-managed-code.md)

> [!TIP]
> Erros e avisos de tempo de build dos analisadores de código serão mostrados apenas se os analisadores estiverem instalados como um pacote NuGet. Os analisadores embutidos (por exemplo, IDE0067 e IDE0068) nunca são executados durante a construção.

Não só os analisadores de código roslyn relatam os mesmos tipos de problemas que a análise de legado, mas facilitam a correção de uma ou todas as ocorrências da violação em seu arquivo ou projeto. Essas ações são denominadas *correções de código*. As correções de código são específicas do IDE; no Visual Studio, eles são implementados como [Ações Rápidas.](../ide/quick-actions.md) Nem todos os diagnósticos do analisador têm uma correção de código associada.

> [!NOTE]
> Antes do lançamento do Visual Studio 2019 16.5, a opção de menu **Analyze** > **Run Code Analysis** executa a análise do legado. Iniciando o Visual Studio 2019 16.5, a opção de menu **Run Code Analysis** executa analisadores baseados em Roslyn para o projeto ou solução selecionados.

Para diferenciar entre violações de analisadores de código e análise de legado na Lista de Erros, olhe para a coluna **Ferramenta.** Se o valor da Ferramenta corresponder a um dos assemblies do analisador no **Gerenciador de Soluções** – por exemplo, **Microsoft.CodeQuality.Analyzers** – a violação será proveniente de um analisador de código. Caso contrário, a violação será proveniente da análise herdada.

![Coluna Ferramenta na Lista de Erros](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> A propriedade **RunCodeAnalysis** MSBuild em um arquivo de projeto se aplica apenas à análise de legado. Se você instalar analisadores, defina **RunCodeAnalysis** como **falso** no arquivo do projeto, para evitar que a análise de legado seja executada após a compilação.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pacote NuGet em comparação com a extensão do VSIX

Os analisadores de código Roslyn podem ser instalados por projeto através de um pacote NuGet. Alguns também estão disponíveis como uma extensão do Visual Studio, nesse caso eles se aplicam a qualquer solução que você abra no Visual Studio. Há algumas importantes diferenças de comportamento entre esses dois métodos de [instalar analisadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Escopo

Se você instalar analisadores como uma extensão do Visual Studio, eles se aplicam no nível da solução e em todas as instâncias do Visual Studio. Se você instalar os analisadores como um pacote NuGet, que é o método preferencial, eles serão aplicáveis somente ao projeto em que o pacote NuGet foi instalado. Em ambientes de equipe, os analisadores instalados como pacotes NuGet estão no escopo para *todos os desenvolvedores* que trabalham nesse projeto.

### <a name="build-errors"></a>Erros de compilação

Para que as regras sejam impostas no tempo de build, incluindo por meio da linha de comando ou como parte de uma build de CI (integração contínua), instale os analisadores como um pacote NuGet. Os erros e avisos do analisador não serão exibidos no relatório de build se você instalar os analisadores como uma extensão.

A imagem a seguir mostra a saída de compilação de linha de comando a partir da construção de um projeto que contém uma violação de regra do analisador:

![Saída do MSBuild com violação de regra](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravidade da regra

Não é possível configurar a gravidade das regras dos analisadores que foram instalados como uma extensão do Visual Studio. Para configurar a [gravidade da regra](../code-quality/use-roslyn-analyzers.md#rule-severity), instale os analisadores como um pacote NuGet.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Instalar analisadores de código no Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usar analisadores de código no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Confira também

- [Perguntas frequentes sobre analisadores](analyzers-faq.md)
- [Gravar seu próprio analisador de código](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK da Plataforma do Compilador .NET](/dotnet/csharp/roslyn-sdk/)
