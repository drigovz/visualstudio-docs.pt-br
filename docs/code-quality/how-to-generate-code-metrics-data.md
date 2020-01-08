---
title: Gerar métricas de código a partir do IDE ou da linha de comando
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a71f507aa5ce524e01b2120594ace634056d0850
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587466"
---
# <a name="how-to-generate-code-metrics-data"></a>Como gerar dados de métricas de código

Você pode gerar dados de métricas de código de três maneiras:

- Instalando [analisadores do FxCop](#fxcop-analyzers-code-metrics-rules) e habilitando as quatro regras de métricas de código (manutenção) que ele contém.

- Escolhendo o comando de menu [ **analisar** > **calcular métricas de código** ](#calculate-code-metrics-menu-command) no Visual Studio.

- Na [linha de comando](#command-line-code-metrics) para C# projetos do e Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Regras de métricas de código de analisadores do FxCop

O [pacote NuGet do FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) inclui várias regras do [analisador](roslyn-analyzers-overview.md) de métricas de código:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506.md)

Essas regras são desabilitadas por padrão, mas você pode habilitá-las de [**Gerenciador de soluções**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) ou em um arquivo de [conjunto de regras](using-rule-sets-to-group-code-analysis-rules.md) . Por exemplo, para habilitar a regra CA1502 como um aviso, o arquivo. RuleSet conterá a seguinte entrada:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuração do

Você pode configurar os limites em que as regras de métricas de código no pacote de analisadores do FxCop são acionadas.

1. Crie um arquivo de texto. Por exemplo, você pode nomeá-lo de *CodeMetricsConfig. txt*.

2. Adicione os limites desejados ao arquivo de texto no seguinte formato:

   ```txt
   CA1502: 10
   ```

   Neste exemplo, a regra [CA1502](ca1502.md) está configurada para ser acionada quando a complexidade de ciclomática de um método for maior que 10.

3. Na janela **Propriedades** do Visual Studio, ou no arquivo de projeto, marque a ação de Build do arquivo de configuração como [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Por exemplo:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Comando de menu calcular métricas de código

Gere métricas de código para um ou todos os seus projetos abertos no IDE usando o menu **analisar** > **calcular métricas de código** .

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Gerar resultados de métricas de código para uma solução inteira

Você pode gerar resultados de métricas de código para uma solução inteira de qualquer uma das seguintes maneiras:

- Na barra de menus, escolha **analisar** > **calcular métricas de código** > **para solução**.

- Em **Gerenciador de soluções**, clique com o botão direito do mouse na solução e escolha **calcular métricas de código**.

- Na janela **resultados de métricas de código** , escolha o botão **calcular métricas de código para solução** .

Os resultados são gerados e a janela **resultados de métricas de código** é exibida. Para exibir os detalhes dos resultados, expanda a árvore na coluna **hierarquia** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Gerar resultados de métricas de código para um ou mais projetos

1. Em **Gerenciador de soluções**, selecione um ou mais projetos.

1. Na barra de menus, escolha **analisar** > **calcular métricas de código** > **para projetos selecionados**.

Os resultados são gerados e a janela **resultados de métricas de código** é exibida. Para exibir os detalhes dos resultados, expanda a árvore na **hierarquia**.

::: moniker range="vs-2017"

> [!NOTE]
> O comando **calcular métricas de código** não funciona para projetos .NET Core e .net Standard. Para calcular as métricas de código para um projeto do .NET Core ou .NET Standard, você pode:
>
> - Calcular as métricas de código na [linha de comando](#command-line-code-metrics) em vez disso
>
> - Atualizar para o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Métricas de código de linha de comando

Você pode gerar dados de métricas de código na linha de C# comando para o e Visual Basic projetos para .NET Framework, .NET Core e aplicativos de .net Standard. Para executar as métricas de código na linha de comando, instale o [pacote NuGet Microsoft. CodeAnalysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) ou crie o executável [métricas. exe](#metricsexe) por conta própria.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pacote NuGet Microsoft. CodeAnalysis. Metrics

A maneira mais fácil de gerar dados de métricas de código a partir da linha de comando é instalar o pacote NuGet [Microsoft. CodeAnalysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) . Depois de instalar o pacote, execute `msbuild /t:Metrics` do diretório que contém o arquivo de projeto. Por exemplo:

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

Você pode substituir o nome do arquivo de saída especificando `/p:MetricsOutputFile=<filename>`. Você também pode obter dados de métricas [de código de estilo herdado](#previous-versions) especificando `/p:LEGACY_CODE_METRICS_MODE=true`. Por exemplo:

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

A saída XML gerada tem o seguinte formato:

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

Se você não quiser instalar o pacote NuGet, poderá gerar e usar o executável de *Metrics. exe* diretamente. Para gerar o executável de *métricas. exe* :

1. Clone o repositório [dotnet/Roslyn-analisadores](https://github.com/dotnet/roslyn-analyzers) .
2. Abra Prompt de Comando do Desenvolvedor do Visual Studio como administrador.
3. Na raiz do repositório **Roslyn-analisadores** , execute o seguinte comando: `Restore.cmd`
4. Altere o diretório para *src\Tools*.
5. Execute o seguinte comando para compilar o projeto de **métricas. csproj** :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Um executável chamado *métricas. exe* é gerado no diretório *artifacts\bin* sob a raiz do repositório.

#### <a name="metricsexe-usage"></a>Uso de métricas. exe

Para executar o *Metrics. exe*, forneça um projeto ou uma solução e um arquivo XML de saída como argumentos. Por exemplo:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modo herdado

Você pode optar por criar *métricas. exe* no *modo herdado*. A versão do modo herdado da ferramenta gera valores de métrica que estão mais próximos que [as versões mais antigas da ferramenta geradas](#previous-versions). Além disso, no modo herdado, o *Metrics. exe* gera métricas de código para o mesmo conjunto de tipos de métodos para os quais as versões anteriores da ferramenta geraram métricas de código. Por exemplo, ele não gera dados de métricas de código para inicializadores de campo e propriedade. O modo herdado é útil para compatibilidade com versões anteriores ou se você tem Gates de check-in de código com base em números de métricas de código. O comando para criar *métricas. exe* no modo herdado é:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Para obter mais informações, consulte [habilitar a geração de métricas de código no modo herdado](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versões anteriores

O Visual Studio 2015 incluía uma ferramenta de métricas de código de linha de comando que também era chamada *métricas. exe*. Esta versão anterior da ferramenta fazia uma análise binária, ou seja, uma análise baseada em assembly. Em vez disso, a nova ferramenta *Metrics. exe* analisa o código-fonte. Como a nova ferramenta *Metrics. exe* é baseada em código-fonte, os resultados das métricas de código de linha de comando são diferentes daqueles gerados pelo IDE do Visual Studio e por versões anteriores do *Metrics. exe*.

A nova ferramenta de métricas de código de linha de comando computa métricas mesmo na presença de erros de código-fonte, desde que a solução e o projeto possam ser carregados.

#### <a name="metric-value-differences"></a>Diferenças de valor de métrica

A métrica de `LinesOfCode` é mais precisa e confiável na nova ferramenta de métricas de código de linha de comando. Ele é independente de qualquer diferença de CodeGen e não é alterado quando o conjunto de ferramentas ou o tempo de execução é alterado. A nova ferramenta conta as linhas reais de código, incluindo comentários e linhas em branco.

Outras métricas como `CyclomaticComplexity` e `MaintainabilityIndex` usam as mesmas fórmulas que as versões anteriores de *métricas. exe*, mas a nova ferramenta conta o número de `IOperations` (instruções de origem lógica) em vez de instruções de Il (linguagem intermediária). Os números serão ligeiramente diferentes daqueles gerados pelo IDE do Visual Studio e por versões anteriores do *Metrics. exe*.

## <a name="see-also"></a>Veja também

- [Use a janela de resultados de métricas de código](../code-quality/working-with-code-metrics-data.md)
- [Valores de métricas de código](../code-quality/code-metrics-values.md)
