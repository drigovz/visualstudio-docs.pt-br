---
title: Análise de código do FxCop e analisadores do FxCop
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431359"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Perguntas frequentes sobre o FxCop e sobre os analisadores do FxCop

Pode ser um pouco confuso entender as diferenças entre os analisadores do FxCop e o FxCop herdado. O objetivo deste artigo é abordar algumas perguntas que você possa ter.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Qual é a diferença entre o FxCop herdado e os analisadores do FxCop?

O FxCop herdado executa análise de pós-build em um assembly compilado. Ele é executado como um executável separado chamado **FxCopCmd.exe**. O FxCopCmd.exe carrega o assembly compilado, executa a análise de código e, em seguida, relata os resultados (ou *diagnóstico*).

Os analisadores do FxCop baseiam-se no .NET Compiler Platform ("Roslyn"). Você [os instala como um pacote NuGet](install-fxcop-analyzers.md#nuget-package) que é referenciado pelo projeto ou pela solução. Os analisadores do FxCop executam a análise baseada em código-fonte durante a execução do compilador. Os analisadores do FxCop são hospedados dentro do processo de compilador, **csc.exe** ou **vbc.exe**, e executam a análise quando o projeto é criado. Os resultados do analisador são relatados junto com os resultados do compilador.

> [!NOTE]
> Também é possível [instalar analisadores do FxCop como uma extensão do Visual Studio](install-fxcop-analyzers.md#vsix). Nesse caso, os analisadores são executados conforme você digita no editor de códigos, mas eles não são executados em tempo de build. Se desejar executar os analisadores do FxCop como parte da CI (integração contínua), instale-os como um pacote NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>O comando Executar análise de código executa analisadores do FxCop?

Antes do visual studio 2019 16.5, quando você seleciona **Analyze** > **Run Code Analysis**, ele executa análise socorrida. Iniciando o Visual Studio 2019 16.5, a opção de menu **Run Code Analysis** executa analisadores baseados em Roslyn para o projeto ou solução selecionados. Se você tiver instalado analisadores FxCop baseados em Roslyn, eles também serão executados. Para obter mais informações, [consulte Como executar a análise de código manualmente para código gerenciado](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>A propriedade do projeto msbuild RunCodeAnalysis executa analisadores?

Não. A propriedade **RunCodeAnalysis** em um arquivo de projeto (por exemplo, *.csproj*) só é usada para executar o FxCop herdado. Ele executa uma tarefa msbuild pós-build que invoca **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Então, como faço para executar analisadores do FxCop?

Para executar os analisadores do FxCop, primeiro [instale o pacote NuGet](install-fxcop-analyzers.md) para eles. Em seguida, crie seu projeto ou solução com base no Visual Studio ou usando msbuild. Os avisos e erros gerados pelos analisadores do FxCop serão exibidos na **Lista de Erros** ou na janela Comando.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Eu recebo aviso CA0507 mesmo depois de instalar o pacote NuGet dos analisadores FxCop

Se você instalou analisadores FxCop, mas continua recebendo aviso CA0507 **""Run Code Analysis" foi preterido em favor dos analisadores FxCop, que são executados durante a compilação"**, você pode precisar definir a propriedade **msbuild RunCodeAnalysis** em seu [arquivo de projeto](../ide/solutions-and-projects-in-visual-studio.md#project-file) como **falsa**. Caso contrário, a análise de legado será executada após cada compilação.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Quais regras foram portadas para analisadores FxCop?

Para obter informações sobre quais regras de análise de legado foram portadas para [analisadores FxCop,](install-fxcop-analyzers.md)consulte [o status da porta de regra Fxcop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Avisos de análise de código são tratados como erros

Se o seu projeto usar a opção de compilação para tratar os avisos como erros, os avisos do analisador FxCop podem aparecer como erros. Para evitar que os avisos de análise de código sejam tratados como erros, siga as etapas da [FAQ de análise de código](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Confira também

- [Visão geral dos analisadores do .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrar para analisadores FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Instalar analisadores do FxCop](install-fxcop-analyzers.md)
