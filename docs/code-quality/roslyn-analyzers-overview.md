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
ms.openlocfilehash: befbb09d347043ae304702618506d193344e23ba
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67195242"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Visão geral dos analisadores do .NET Compiler Platform

Os analisadores da .NET Compiler Platform ("Roslyn") analisam seu código quanto a estilo, qualidade e facilidade de manutenção, design e outras questões. O Visual Studio inclui um conjunto interno de analisadores que analisam o código C# e Visual Basic durante a digitação. Configure as preferências para esses analisadores internos na página [Opções do editor de texto](../ide/code-styles-and-code-cleanup.md) ou em um [arquivo .editorconfig](../ide/editorconfig-code-style-settings-reference.md). Instale outros analisadores como uma extensão do Visual Studio ou como um pacote NuGet.

Se um analisador encontrar violações de regra, elas serão relatadas no editor de códigos (como uma *linha ondulada* embaixo do código transgressor) e na janela **Lista de Erros**.

Muitas regras do analisador ou *diagnósticos* têm uma ou mais *correções de código* associadas que podem ser aplicadas para corrigir o problema. Cada diagnóstico do analisador inserido no Visual Studio tem uma correção de código associada. As correções de código são mostradas no menu do ícone de lâmpada, juntamente com outros tipos de [Ações rápidas](../ide/quick-actions.md). Para saber mais sobre essas correções de código, confira [Ações rápidas comuns](../ide/common-quick-actions.md).

![Violação do analisador e correção de código de Ação Rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analisadores do Roslyn vs. análise de código estático

Os Analisadores do .NET Compiler Platform ("Roslyn") substituirão eventualmente a [análise de código estático](../code-quality/code-analysis-for-managed-code-overview.md) por código gerenciado. Muitas das regras de análise de código estático já foram reescritas como diagnóstico de analisador do Roslyn.

Como violações de regra de análise de código estático, as violações de analisador do Roslyn são exibidas na **Lista de Erros**. Além disso, as violações de analisador do Roslyn também são mostradas no editor de códigos, como *linhas onduladas* abaixo do código transgressor. A cor da linha ondulada depende da [configuração de gravidade](../code-quality/use-roslyn-analyzers.md#rule-severity) da regra. A captura de tela a seguir mostra três violações&mdash;uma vermelha, uma verde e uma cinza:

![Linhas onduladas no editor de códigos](media/diagnostics-severity-colors.png)

Os analisadores do Roslyn analisam código em tempo de build, como análise de código estático, se habilitada, mas também em tempo real conforme você digita. Se você habilitar [análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis), os analisadores do Roslyn também fornecerão análise em tempo de design dos arquivos de código que não estão abertos no editor.

> [!TIP]
> Erros e avisos de tempo de build de analisadores do Roslyn serão mostrados apenas se os analisadores estiverem instalados como um pacote NuGet.

Os analisadores do Roslyn não só comunicam os mesmos tipos de problemas que a análise de código estático, mas também facilitam a correção de uma ou todas as ocorrências da violação no seu arquivo ou projeto. Essas ações são denominadas *correções de código*. As correções de código são específicas do IDE; no Visual Studio, elas são implementadas como [Ações rápidas](../ide/quick-actions.md). Nem todos os diagnósticos do analisador têm uma correção de código associada.

> [!NOTE]
> As seguintes opções da interface do usuário se aplicam somente à análise de código estático:
>
> - A opção de menu **Analisar** > **Executar Análise de Código**.
> - As caixas de seleção **Habilitar análise de código no build** e **Suprimir resultados do código gerado** na guia **Análise de Código** das páginas de propriedades de um projeto (essas opções não têm efeito nos analisadores do Roslyn).

Para diferenciar entre as violações de analisadores do Roslyn e análise de código estático na **Lista de Erros**, examine a coluna **Ferramenta**. Se o valor Ferramenta corresponder a um dos assemblies do analisador no **Gerenciador de Soluções**, por exemplo **Microsoft.CodeQuality.Analyzers**, a violação será proveniente de um analisador do Roslyn. Caso contrário, a violação será proveniente da análise de código estático.

![Coluna Ferramenta na Lista de Erros](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> A propriedade msbuild **RunCodeAnalysis** em um arquivo de projeto se aplica somente à análise de código estático. Se você instalar analisadores, defina **RunCodeAnalysis** como **false** no seu arquivo de projeto para evitar que a análise de código estático seja executada após a compilação.
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

### <a name="categories"></a>Categorias

Veja a seguir os diferentes tipos de analisador que ajudam a analisar seu código. 

- Analisadores recomendados pela Microsoft: [Analisadores FxCop](../code-quality/fxcop-analyzers.yml)
- Analisadores de IDE do Visual Studio: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Analisadores de terceiros: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/), [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Instalar Analisadores do Roslyn no Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usar Analisadores do Roslyn no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Consulte também

- [Perguntas frequentes sobre analisadores](analyzers-faq.md)
- [Escrever seu próprio analisador do Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK do .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
