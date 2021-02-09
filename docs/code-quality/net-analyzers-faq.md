---
title: Análise de código do FxCop (análise binária) e analisadores .NET (análise de origem)
ms.date: 09/06/2018
description: Entenda a diferença entre o FxCop (análise binária) herdado e os analisadores do .NET (análise de origem) no Visual Studio. Consulte as respostas para perguntas sobre como usar esses analisadores.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867757"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Perguntas frequentes sobre os analisadores herdados do FxCop e do .NET

Pode ser um pouco confuso entender as diferenças entre o FxCop (análise binária) herdado e os analisadores .NET (análise de origem). O objetivo deste artigo é abordar algumas perguntas que você possa ter.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Qual é a diferença entre os analisadores do FxCop e do .NET herdados?

O FxCop herdado executa análise de pós-build em um assembly compilado. Ele é executado como um executável separado chamado **FxCopCmd.exe**. O FxCopCmd.exe carrega o assembly compilado, executa a análise de código e, em seguida, relata os resultados (ou *diagnóstico*).

Os analisadores .NET são baseados na .NET Compiler Platform ("Roslyn"). Você [os habilita no SDK do .net ou os instala como um pacote NuGet](install-net-analyzers.md) referenciado pelo projeto ou solução. Os analisadores executam a análise baseada em código-fonte durante a execução do compilador. Os analisadores são hospedados no processo do compilador, seja **csc.exe** ou **vbc.exe** e executam a análise quando o projeto é compilado. Os resultados do analisador são relatados junto com os resultados do compilador.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Qual é a diferença entre analisadores do FxCop e analisadores .NET?

Ambos os analisadores do FxCop e os analisadores do .NET referem-se às implementações do analisador .NET Compiler Platform ("Roslyn") das regras de AC do FxCop. Antes do Visual Studio 2019 16,8 e do .NET 5,0, esses analisadores foram fornecidos como `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacote NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partir do Visual Studio 2019 16,8 e do .NET 5,0, esses analisadores estão [incluídos no SDK do .net](/dotnet/fundamentals/code-analysis/overview). Eles também estão disponíveis como `Microsoft.CodeAnalysis.NetAnalyzers` [pacote NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Considere [migrar dos analisadores do FxCop para os analisadores do .net](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>O comando executar análise de código executa analisadores .NET?

Antes do Visual Studio 2019 versão 16,5, quando você seleciona **analisar**  >  **executar análise de código**, ele executa a análise herdada. Iniciando o Visual Studio 2019 16,5, a opção de menu **executar análise de código** executa analisadores baseados em Roslyn para o projeto ou solução selecionada. Se você tiver instalado os analisadores do .NET, eles também serão executados. Para obter mais informações, consulte [como executar a análise de código manualmente para código gerenciado](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>A propriedade do projeto msbuild RunCodeAnalysis executa analisadores?

Não. A propriedade **RunCodeAnalysis** em um arquivo de projeto (por exemplo, *.csproj*) só é usada para executar o FxCop herdado. Ele executa uma tarefa msbuild pós-build que invoca **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Então, como executar os analisadores do .NET?

Para executar os analisadores do .NET, primeiro [habilite-os no SDK do .net ou instale-os como um pacote NuGet](install-net-analyzers.md). Em seguida, crie seu projeto ou solução com base no Visual Studio ou usando msbuild. Os avisos e erros que os analisadores de Roslyn geram aparecerão no **lista de erros** ou na janela de comando.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Eu obtenho o aviso CA0507 mesmo depois de instalar o pacote NuGet dos analisadores .NET

Se você instalou os analisadores do .NET, mas continuar a obter o aviso CA0507 **"" executar análise de código "foi preterido em favor dos analisadores do FxCop, que são executados durante a compilação"**, talvez seja necessário definir a Propriedade MSBuild do **RunCodeAnalysis** no [arquivo de projeto](../ide/solutions-and-projects-in-visual-studio.md#project-file) como **false**. Caso contrário, a análise herdada será executada após cada compilação.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Quais regras foram transportadas para os analisadores .NET?

Para obter informações sobre quais regras de análise herdadas foram modeladas para os analisadores do .NET, consulte [status da porta da regra do FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Os avisos de análise de código são tratados como erros

Se seu projeto usar a opção de compilação para tratar avisos como erros, os avisos do analisador poderão aparecer como erros. Para impedir que avisos de análise de código sejam tratados como erros, siga as etapas em [perguntas frequentes sobre análise de código](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Confira também

- [Visão geral dos analisadores do .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrar para analisadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Instalar analisadores de .NET](install-net-analyzers.md)
