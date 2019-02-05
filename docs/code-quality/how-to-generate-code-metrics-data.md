---
title: Gerar as métricas de código do IDE ou na linha de comando
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91e32cdae7310a99021946315279736bddb094a8
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690132"
---
# <a name="how-to-generate-code-metrics-data"></a>Como: Gerar dados de métricas de código

Você pode gerar resultados de métricas de código para um ou mais projetos ou uma solução inteira. As métricas de código estão disponível dentro do ambiente de desenvolvimento interativo (IDE) do Visual Studio e, para C# e projetos do Visual Basic, na linha de comando.

Além disso, você pode instalar um [pacote do NuGet](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) que inclui quatro métricas de código [analisador](roslyn-analyzers-overview.md) regras: CA1501, CA1502, CA1505 e CA1506. Essas regras são desabilitadas por padrão, mas você pode habilitá-las a partir **Gerenciador de soluções** ou em um [conjunto de regras](using-rule-sets-to-group-code-analysis-rules.md) arquivo.

## <a name="visual-studio-ide-code-metrics"></a>Métricas de código do Visual Studio IDE

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Gerar resultados de métricas de código para uma solução inteira

Você pode gerar resultados de métricas de código para uma solução inteira em qualquer uma das seguintes maneiras:

- Na barra de menus, escolha **Analyze** > **calcular métricas de código** > **para solução**.

- Na **Gerenciador de soluções**, a solução com o botão direito e, em seguida, escolha **calcular métricas de código**.

- No **resultados de métricas de código** janela, escolha o **calcular métricas de código para solução** botão.

Os resultados são gerados e o **resultados de métricas de código** janela é exibida. Para exibir os detalhes de resultados, expanda a árvore na **hierarquia** coluna.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Gerar resultados de métricas de código para um ou mais projetos

1. Na **Gerenciador de soluções**, selecione um ou mais projetos.

1. Na barra de menus, escolha **Analyze** > **calcular métricas de código** > **para projetos selecionados**.

Os resultados são gerados e o **resultados de métricas de código** janela é exibida. Para exibir os detalhes de resultados, expanda a árvore na **hierarquia**.

## <a name="command-line-code-metrics"></a>Métricas de código de linha de comando

Você pode gerar dados de métricas de código da linha de comando para C# e projetos do Visual Basic para aplicativos do .NET Framework, .NET Core e .NET Standard. Para executar as métricas de código da linha de comando, instale o [pacote do Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) ou compilar a [Metrics.exe](#metricsexe) executável por conta própria.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pacote do Microsoft.CodeAnalysis.Metrics NuGet

A maneira mais fácil de gerar dados de métricas de código da linha de comando é instalando o [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) pacote do NuGet. Depois de instalar o pacote, execute `msbuild /t:Metrics` do diretório que contém seu arquivo de projeto. Por exemplo:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Você pode substituir o nome do arquivo de saída especificando `/p:MetricsOutputFile=<filename>`. Você também pode obter [estilo herdado](#previous-versions) dados de métricas de código, especificando `/p:LEGACY_CODE_METRICS_MODE=true`. Por exemplo:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Saída de métricas de código

A saída XML gerada recebe o seguinte formato:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Metrics.exe

Se você não quiser instalar o pacote do NuGet, você pode gerar e usar o *Metrics.exe* executável diretamente. Para gerar a *Metrics.exe* executável:

1. Clone o [dotnet/roslyn-analyzers](https://github.com/dotnet/roslyn-analyzers) repositório.
2. Abra o Prompt de comando do desenvolvedor para Visual Studio como administrador.
3. Da raiz de **analisadores de roslyn** repositório, execute o seguinte comando: `Restore.cmd`
4. Altere o diretório para *src\Tools*.
5. Execute o seguinte comando para criar o **Metrics.csproj** projeto:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Um arquivo executável chamado *Metrics.exe* é gerado na *artifacts\bin* diretório sob a raiz do repositório.

#### <a name="metricsexe-usage"></a>Uso de Metrics.exe

Para executar *Metrics.exe*, fornecer um projeto ou solução e um XML de saída de arquivo como argumentos. Por exemplo:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modo herdado

Você pode optar por compilar *Metrics.exe* na *modo herdado*. A versão do modo herdado da ferramenta gera valores de métrica que estão mais próximos à qual [versões mais antigas da ferramenta gerada](#previous-versions). Além disso, no modo herdado, *Metrics.exe* gera métricas de código para o mesmo conjunto de método de tipos que as métricas de código gerada de ferramenta para as versões anteriores. Por exemplo, ele não gera dados de métricas de código para inicializadores de campo e propriedade. Modo herdado é útil para versões anteriores compatibilidade ou, se você tiver portões de check-in do código com base em métricas de código números. O comando para compilar *Metrics.exe* no modo herdado é:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Para obter mais informações, consulte [habilitar a geração de métricas de código no modo herdado](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versões anteriores

As versões anteriores do Visual Studio, incluindo o Visual Studio 2015, incluíam uma ferramenta de métricas de código de linha de comando que também foi chamada *Metrics.exe*. Nesta versão anterior da ferramenta fez uma análise binária, ou seja, uma análise baseada em assembly. A nova ferramenta analisa o código-fonte em vez disso. Como a nova ferramenta de métricas de código de linha de comando é baseado em código de origem, os resultados são diferentes para o que é gerado por versões anteriores do *Metrics.exe* e dentro do IDE do Visual Studio 2017.

A nova ferramenta de métricas de código de linha de comando calcula métricas mesmo na presença de erros de código fonte, desde que a solução e projeto podem ser carregados.

#### <a name="metric-value-differences"></a>Diferenças de valor de métrica

O `LinesOfCode` métrica é mais precisos e confiáveis na nova ferramenta de métricas de código de linha de comando. Ele é independente de quaisquer diferenças de geração de código e não muda quando o conjunto de ferramentas ou tempo de execução é alterado. A nova ferramenta conta real de linhas de código, incluindo comentários e linhas em branco.

Outras métricas, como `CyclomaticComplexity` e `MaintainabilityIndex` usar as mesmas fórmulas como as versões anteriores do *Metrics.exe*, mas a nova ferramenta conta o número de `IOperations` (instruções de lógica de código-fonte) em vez de intermediário instruções de IL (linguagem). Os números serão ligeiramente diferentes das versões anteriores do *Metrics.exe* e dos resultados de métricas de código do IDE do Visual Studio 2017.

## <a name="see-also"></a>Consulte também

- [Use a janela de resultados de métricas de código](../code-quality/working-with-code-metrics-data.md)
- [Valores de métricas de código](../code-quality/code-metrics-values.md)
