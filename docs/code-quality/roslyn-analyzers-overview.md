---
title: Análise de código usando os analisadores do Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 844b9475ea59ba15ac96d3cbe19523f5cba63c72
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999986"
---
# <a name="overview-of-source-code-analyzers"></a>Visão geral dos analisadores de código-fonte

Os analisadores de código do .NET Compiler Platform ("Roslyn" C# ) inspecionam seu código de Visual Basic de estilo, qualidade e facilidade de manutenção, design e outros problemas.

- Alguns analisadores são integrados ao Visual Studio. A ID de diagnóstico ou o código para esses analisadores é do formato IDExxxx, por exemplo, IDE0067. A maioria desses analisadores internos inspeciona o [estilo de código](../ide/code-styles-and-code-cleanup.md)e você pode configurar preferências na página de [Opções do editor de texto](../ide/code-styles-and-code-cleanup.md) ou em um [arquivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Alguns analisadores internos analisam a qualidade do código.

- Você pode instalar analisadores adicionais como um pacote NuGet ou uma extensão do Visual Studio. Por exemplo:

  - [Analisadores do FxCop](../code-quality/install-fxcop-analyzers.md), analisadores de qualidade de código recomendados pela Microsoft
  - Analisadores de terceiros, como [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [analisadores de xUnit](https://www.nuget.org/packages/xunit.analyzers/)e [analisador de sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Se violações de regra forem encontradas por um analisador, elas serão relatadas no editor de códigos (como um *rabisco* no código incorreto) e na janela de lista de erros.

Muitas regras do analisador ou *diagnósticos* têm uma ou mais *correções de código* associadas que podem ser aplicadas para corrigir o problema. Cada diagnóstico do analisador inserido no Visual Studio tem uma correção de código associada. As correções de código são mostradas no menu do ícone de lâmpada, juntamente com outros tipos de [Ações rápidas](../ide/quick-actions.md). Para saber mais sobre essas correções de código, confira [Ações rápidas comuns](../ide/common-quick-actions.md).

![Violação do analisador e correção de código de Ação Rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Análise de código-fonte versus análise herdada

A análise de origem por analisadores Roslyn substitui a [análise herdada](../code-quality/code-analysis-for-managed-code-overview.md) para código gerenciado. Muitas das regras de análise herdadas já foram reescritas como analisadores de código Roslyn. Para modelos de projeto mais recentes, como projetos .NET Core e .NET Standard, a análise herdada ainda não está disponível.

Como violações de regras de análise herdadas, as violações de análise de código-fonte aparecem na janela Lista de Erros no Visual Studio. Além disso, as violações de análise de código-fonte também aparecem no editor de códigos como *ondulado* no código incorreto. A cor da linha ondulada depende da [configuração de gravidade](../code-quality/use-roslyn-analyzers.md#rule-severity) da regra. A imagem a seguir mostra três violações @ no__t-0one vermelho, um verde e um cinza:

![Rabiscos no editor de códigos do Visual Studio](media/diagnostics-severity-colors.png)

Os analisadores de código inspecionam o código no momento da compilação, como a análise herdada, se ela estiver habilitada, mas também ao vivo conforme você digita. Se você habilitar a [análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis), os analisadores de código também fornecerão análise em tempo de design dos arquivos de código que não estão abertos no editor.

> [!TIP]
> Erros e avisos de tempo de build dos analisadores de código serão mostrados apenas se os analisadores estiverem instalados como um pacote NuGet. Os analisadores internos (por exemplo, IDE0067 e IDE0068) nunca são executados durante a compilação.

Não apenas os analisadores de código Roslyn relatam os mesmos tipos de problemas que a análise herdada faz, mas eles facilitam a correção de uma ou de todas as ocorrências da violação em seu arquivo ou projeto. Essas ações são denominadas *correções de código*. As correções de código são específicas do IDE; no Visual Studio, eles são implementados como [ações rápidas](../ide/quick-actions.md). Nem todos os diagnósticos do analisador têm uma correção de código associada.

> [!NOTE]
> A opção de menu **analisar** > **executar análise de código** aplica-se somente à análise herdada.

Para diferenciar as violações dos analisadores de código e da análise herdada no Lista de Erros, examine a coluna de **ferramentas** . Se o valor da Ferramenta corresponder a um dos assemblies do analisador no **Gerenciador de Soluções** – por exemplo, **Microsoft.CodeQuality.Analyzers** – a violação será proveniente de um analisador de código. Caso contrário, a violação será proveniente da análise herdada.

![Coluna Ferramenta na Lista de Erros](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> A Propriedade MSBuild do **RunCodeAnalysis** em um arquivo de projeto aplica-se somente à análise herdada. Se você instalar os analisadores, defina **RunCodeAnalysis** como **false** no arquivo de projeto, para impedir que a análise herdada seja executada após a compilação.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pacote NuGet em comparação com a extensão do VSIX

Os analisadores de código Roslyn podem ser instalados por projeto por meio de um pacote NuGet. Alguns também estão disponíveis como uma extensão do Visual Studio; nesse caso, eles se aplicam a qualquer solução que você abrir no Visual Studio. Há algumas importantes diferenças de comportamento entre esses dois métodos de [instalar analisadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Escopo

Se você instalar analisadores como uma extensão do Visual Studio, eles serão aplicados no nível da solução e em todas as instâncias do Visual Studio. Se você instalar os analisadores como um pacote NuGet, que é o método preferencial, eles serão aplicáveis somente ao projeto em que o pacote NuGet foi instalado. Em ambientes de equipe, os analisadores instalados como pacotes NuGet estão no escopo para *todos os desenvolvedores* que trabalham nesse projeto.

### <a name="build-errors"></a>Erros de build

Para que as regras sejam impostas no tempo de build, incluindo por meio da linha de comando ou como parte de uma build de CI (integração contínua), instale os analisadores como um pacote NuGet. Os erros e avisos do analisador não serão exibidos no relatório de build se você instalar os analisadores como uma extensão.

A imagem a seguir mostra a saída da compilação de linha de comando da criação de um projeto que contém uma violação de regra do analisador:

![Saída do MSBuild com violação de regra](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravidade da regra

Você não pode configurar a severidade de regras de analisadores que foram instalados como uma extensão do Visual Studio. Para configurar a [gravidade da regra](../code-quality/use-roslyn-analyzers.md#rule-severity), instale os analisadores como um pacote NuGet.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Instalar analisadores de código no Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usar analisadores de código no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Consulte também

- [Perguntas frequentes sobre analisadores](analyzers-faq.md)
- [Gravar seu próprio analisador de código](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK do .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
