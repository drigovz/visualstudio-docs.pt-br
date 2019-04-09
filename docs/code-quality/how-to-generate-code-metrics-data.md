---
title: Gerar as métricas de código do IDE ou na linha de comando
ms.date: 11/02/2018
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
ms.openlocfilehash: 4275e92b21289c5cf1e3243b2bc782a9e0821fde
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232743"
---
# <a name="how-to-generate-code-metrics-data"></a>Como: Gerar dados de métricas de código

Você pode gerar dados de métricas de código de três maneiras:

- Instalando [analisadores FxCop](#fxcop-analyzers-code-metrics-rules) e habilitar as regras de métricas (facilidade de manutenção) do código de quatro nele.

- Escolhendo a [ **Analyze** > **calcular métricas de código** ](#calculate-code-metrics-menu-command) comando de menu dentro do Visual Studio.

- Dos [linha de comando](#command-line-code-metrics) para C# e projetos do Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Regras de métricas de código de analisadores FxCop

O [pacote do FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) inclui várias métricas de código [analisador](roslyn-analyzers-overview.md) regras:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502-avoid-excessive-complexity.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

Essas regras são desabilitadas por padrão, mas você pode habilitá-las a partir [ **Gerenciador de soluções** ](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) ou em um [conjunto de regras](using-rule-sets-to-group-code-analysis-rules.md) arquivo. Por exemplo, para habilitar a regra CA1502 como um aviso, seu arquivo. RuleSet conteria a seguinte entrada:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuração

Você pode configurar os limites em que as regras de métricas de código em que os analisadores FxCop empacotar incêndio.

1. Crie um arquivo de texto. Por exemplo, você pode chamá-lo *CodeMetricsConfig.txt*.

2. Adicione os limites desejados para o arquivo de texto no seguinte formato:

   ```txt
   CA1502: 10
   ```

   Neste exemplo, de regra [CA1502](ca1502-avoid-excessive-complexity.md) está configurado para ser acionado quando a complexidade ciclomática do método é maior que 10.

3. No **propriedades** janela do Visual Studio ou no arquivo de projeto, marcar a ação de build do arquivo de configuração como [ **AdditionalFiles**](../ide/build-actions.md#build-action-values). Por exemplo:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Calcular o comando de menu de métricas de código

Gerar as métricas de código para um ou todos os seus projetos abertos no IDE usando o **Analyze** > **calcular métricas de código** menu.

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

::: moniker range="vs-2017"

> [!NOTE]
> O **calcular métricas de código** comando não funciona para projetos .NET Core e .NET Standard. Para calcular métricas de código para um projeto .NET Core ou .NET Standard, você pode:
>
> - calcular métricas de código a partir de [linha de comando](#command-line-code-metrics) em vez disso
>
> - Atualizar para o [2019 do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

::: moniker-end

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

Visual Studio 2015 incluiu uma ferramenta de métricas de código de linha de comando que também foi chamada *Metrics.exe*. Nesta versão anterior da ferramenta fez uma análise binária, ou seja, uma análise baseada em assembly. O novo *Metrics.exe* ferramenta analisa o código-fonte em vez disso. Porque o novo *Metrics.exe* ferramenta é métricas de código de linha de comando, com base no código de origem resultados são diferentes daqueles gerados pelo IDE do Visual Studio e por versões anteriores do *Metrics.exe*.

A nova ferramenta de métricas de código de linha de comando calcula métricas mesmo na presença de erros de código fonte, desde que a solução e projeto podem ser carregados.

#### <a name="metric-value-differences"></a>Diferenças de valor de métrica

O `LinesOfCode` métrica é mais precisos e confiáveis na nova ferramenta de métricas de código de linha de comando. Ele é independente de quaisquer diferenças de geração de código e não muda quando o conjunto de ferramentas ou tempo de execução é alterado. A nova ferramenta conta real de linhas de código, incluindo comentários e linhas em branco.

Outras métricas, como `CyclomaticComplexity` e `MaintainabilityIndex` usar as mesmas fórmulas como as versões anteriores do *Metrics.exe*, mas a nova ferramenta conta o número de `IOperations` (instruções de lógica de código-fonte) em vez de intermediário instruções de IL (linguagem). Os números serão ligeiramente diferentes daqueles gerados pelo IDE do Visual Studio e por versões anteriores do *Metrics.exe*.

## <a name="see-also"></a>Consulte também

- [Use a janela de resultados de métricas de código](../code-quality/working-with-code-metrics-data.md)
- [Valores de métricas de código](../code-quality/code-metrics-values.md)
