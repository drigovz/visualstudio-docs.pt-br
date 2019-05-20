---
title: Análise de código do FxCop e analisadores do FxCop
ms.date: 09/06/2018
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab7816e7e1472101f0e84c05a4975f19e3902e27
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613554"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Perguntas frequentes sobre o FxCop e sobre os analisadores do FxCop

Pode ser um pouco confuso entender as diferenças entre os analisadores do FxCop e o FxCop herdado. O objetivo deste artigo é abordar algumas perguntas que você possa ter.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Qual é a diferença entre o FxCop herdado e os analisadores do FxCop?

O FxCop herdado executa análise de pós-build em um assembly compilado. Ele é executado como um executável separado chamado **FxCopCmd.exe**. O FxCopCmd.exe carrega o assembly compilado, executa a análise de código e, em seguida, relata os resultados (ou *diagnóstico*).

Os analisadores do FxCop baseiam-se no .NET Compiler Platform ("Roslyn"). Você [os instala como um pacote NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) que é referenciado pelo projeto ou pela solução. Os analisadores do FxCop executam a análise baseada em código-fonte durante a execução do compilador. Os analisadores do FxCop são hospedados dentro do processo de compilador, **csc.exe** ou **vbc.exe**, e executam a análise quando o projeto é criado. Os resultados do analisador são relatados junto com os resultados do compilador.

> [!NOTE]
> Também é possível [instalar analisadores do FxCop como uma extensão do Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). Nesse caso, os analisadores são executados conforme você digita no editor de códigos, mas eles não são executados em tempo de build. Se desejar executar os analisadores do FxCop como parte da CI (integração contínua), instale-os como um pacote NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>O comando Executar análise de código executa analisadores do FxCop?

Nº Quando você seleciona **Analisar** > **Executar Análise de Código**, ele executa a análise de código estático ou o FxCop herdado. **Executar análise de código** não tem efeito sobre os analisadores baseados em Roslyn, incluindo os analisadores do FxCop baseados em Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>A propriedade do projeto msbuild RunCodeAnalysis executa analisadores?

Nº A propriedade **RunCodeAnalysis** em um arquivo de projeto (por exemplo, *.csproj*) só é usada para executar o FxCop herdado. Ele executa uma tarefa msbuild pós-build que invoca **FxCopCmd.exe**. Isso é equivalente a selecionar **Analisar** > **Executar análise de código** no Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Então, como faço para executar analisadores do FxCop?

Para executar os analisadores do FxCop, primeiro [instale o pacote NuGet](install-fxcop-analyzers.md) para eles. Em seguida, crie seu projeto ou solução com base no Visual Studio ou usando msbuild. Os avisos e erros gerados pelos analisadores do FxCop serão exibidos na **Lista de Erros** ou na janela Comando.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Eu recebo aviso CA0507 mesmo depois de instalar o pacote NuGet dos analisadores FxCop

Se você instalou os analisadores FxCop, mas continua recebendo o aviso CA0507 **"Executar análise de código" foi preterido a favor dos analisadores FxCop, que são executados durante o build"**, talvez você precise definir a propriedade do msbuild **RunCodeAnalysis** no arquivo de projeto como **false**. Caso contrário, a análise de código estático será executada após cada compilação.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores do .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Introdução aos analisadores](fxcop-analyzers.yml)
- [Instalar analisadores do FxCop](install-fxcop-analyzers.md)
