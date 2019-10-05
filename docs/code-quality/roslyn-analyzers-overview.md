---
title: Análise de código usando os analisadores do Roslyn
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: af237fbc3ce7bcf098cd47065ed18d1dfd7f20a2
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975004"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>Visão geral dos analisadores de código do .NET Compiler Platform

Os analisadores da .NET Compiler Platform ("Roslyn") analisam seu código quanto a estilo, qualidade e facilidade de manutenção, design e outras questões. O Visual Studio inclui um conjunto interno de analisadores que analisam o código C# e Visual Basic durante a digitação. Configure as preferências para esses analisadores internos na página [Opções do editor de texto](../ide/code-styles-and-code-cleanup.md) ou em um [arquivo .editorconfig](../ide/editorconfig-code-style-settings-reference.md). Instale outros analisadores como uma extensão do Visual Studio ou como um pacote NuGet.

Se um analisador encontrar violações de regra, elas serão relatadas no editor de códigos (como uma *linha ondulada* embaixo do código transgressor) e na janela **Lista de Erros**.

Muitas regras do analisador ou *diagnósticos* têm uma ou mais *correções de código* associadas que podem ser aplicadas para corrigir o problema. Cada diagnóstico do analisador inserido no Visual Studio tem uma correção de código associada. As correções de código são mostradas no menu do ícone de lâmpada, juntamente com outros tipos de [Ações rápidas](../ide/quick-actions.md). Para saber mais sobre essas correções de código, confira [Ações rápidas comuns](../ide/common-quick-actions.md).

![Violação do analisador e correção de código de Ação Rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>Análise baseada no .NET Compiler Platform versus análise herdada

Eventualmente, a análise de código do "Roslyn" (.NET Compiler Platform) substituirá a [análise herdada](../code-quality/code-analysis-for-managed-code-overview.md) por códigos gerenciados. Muitas das regras de análise herdada já foram reescritas como analisadores de código baseados no .NET Compiler Platform.

Assim como as violações de regras das análises herdadas, as violações de análise de código baseadas no .NET Compiler Platform aparecem na janela da Lista de Erros do Visual Studio. Além disso, as violações de análise de código baseadas no .NET Compiler Platform também são mostradas no editor de códigos como *linhas onduladas* abaixo do código com a vioalção. A cor da linha ondulada depende da [configuração de gravidade](../code-quality/use-roslyn-analyzers.md#rule-severity) da regra. A captura de tela a seguir mostra três violações&mdash;uma vermelha, uma verde e uma cinza:

![Linhas onduladas no editor de códigos](media/diagnostics-severity-colors.png)

Os analisadores de código baseados do .NET Compiler Platform analisam código em tempo de build, como a análise herdada, se habilitada, mas também em tempo real, à medida que você digita. Se você habilitar a [análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis), os analisadores de código também fornecerão análise em tempo de design dos arquivos de código que não estão abertos no editor.

> [!TIP]
> Erros e avisos de tempo de build dos analisadores de código serão mostrados apenas se os analisadores estiverem instalados como um pacote NuGet.

Os analisadores de código baseados no .NET Compiler Platform não só comunicam os mesmos tipos de problemas que a análise herdada, mas também facilitam a correção de uma ou todas as ocorrências da violação em seu arquivo ou projeto. Essas ações são denominadas *correções de código*. As correções de código são específicas do IDE; no Visual Studio, elas são implementadas como [Ações rápidas](../ide/quick-actions.md). Nem todos os diagnósticos do analisador têm uma correção de código associada.

> [!NOTE]
> As seguintes opções da interface do usuário se aplicam somente à análise herdada:
>
> - A opção de menu **Analisar** > **Executar Análise de Código**.
> - As caixas de seleção **executar em Compilar** e **suprimir resultados de código gerado** na guia **análise de código** das páginas de propriedades de um projeto.

Para diferenciar entre as violações dos analisadores de código e da análise herdada na janela da Lista de Erros, examine a coluna **Ferramenta**. Se o valor da Ferramenta corresponder a um dos assemblies do analisador no **Gerenciador de Soluções** – por exemplo, **Microsoft.CodeQuality.Analyzers** – a violação será proveniente de um analisador de código. Caso contrário, a violação será proveniente da análise herdada.

![Coluna Ferramenta na Lista de Erros](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> A propriedade **RunCodeAnalysis** do msbuild em um arquivo de projeto se aplica somente à análise herdada. Se você instalar analisadores, defina **RunCodeAnalysis** como **false** no arquivo de projeto para evitar que a análise herdada seja executada após o build.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pacote NuGet em comparação com a extensão do VSIX

Os analisadores do .NET Compiler Platform podem ser instalados por projeto por meio de um pacote NuGet ou em todo o Visual Studio como uma extensão dele. Há algumas importantes diferenças de comportamento entre esses dois métodos de [instalar analisadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Escopo

Se você instalar analisadores como uma extensão do Visual Studio, então aplique, no nível da solução, a todas as instâncias do Visual Studio. Se você instalar os analisadores como um pacote NuGet, que é o método preferencial, eles serão aplicáveis somente ao projeto em que o pacote NuGet foi instalado. Em ambientes de equipe, os analisadores instalados como pacotes NuGet estão no escopo para *todos os desenvolvedores* que trabalham nesse projeto.

### <a name="build-errors"></a>Erros de build

Para que as regras sejam impostas no tempo de build, incluindo por meio da linha de comando ou como parte de uma build de CI (integração contínua), instale os analisadores como um pacote NuGet. Os erros e avisos do analisador não serão exibidos no relatório de build se você instalar os analisadores como uma extensão.

A captura de tela a seguir mostra a saída de build da linha de comando da criação de um projeto que contém uma violação de regra de analisador:

![Saída do MSBuild com violação de regra](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravidade da regra

Não é possível definir a gravidade das regras de analisadores que foram instalados como uma extensão do Visual Studio. Para configurar a [gravidade da regra](../code-quality/use-roslyn-analyzers.md#rule-severity), instale os analisadores como um pacote NuGet.

## <a name="categories"></a>Categories

Veja a seguir os diferentes tipos de analisador que ajudam a analisar o código:

- Analisadores recomendados pela Microsoft: [Analisadores FxCop](../code-quality/fxcop-analyzers.yml)
- Analisadores de IDE do Visual Studio: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Analisadores de terceiros: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Instalar analisadores de código no Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usar analisadores de código no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Consulte também

- [Perguntas frequentes sobre analisadores](analyzers-faq.md)
- [Gravar seu próprio analisador de código](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK do .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
