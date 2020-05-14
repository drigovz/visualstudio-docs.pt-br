---
title: Gerar métricas de código a partir da linha IDE ou de comando
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
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649309"
---
# <a name="how-to-generate-code-metrics-data"></a>Como: Gerar dados de métricas de código

Você pode gerar dados de métricas de código de três maneiras:

- Instalando [analisadores FxCop](#fxcop-analyzers-code-metrics-rules) e habilitando as quatro regras de métricas de código (manutenção) que ele contém.

- Ao escolher o comando [ **Analisar** > o](#calculate-code-metrics-menu-command) menu Métricas de Código de Cálculo dentro do Visual Studio.

- Da [linha de comando](#command-line-code-metrics) para projetos C# e Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Análisedores fxcop regras métricas de código

O [pacote FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) inclui várias regras [de análise de](roslyn-analyzers-overview.md) métricas de código:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Essas regras são desativadas por padrão, mas você pode habilitá-las no [**Solution Explorer**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) ou em um arquivo definido [por regras.](using-rule-sets-to-group-code-analysis-rules.md) Por exemplo, para habilitar a regra CA1502 como um aviso, seu arquivo .ruleset conteria a seguinte entrada:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuração

Você pode configurar os limiares nos quais as métricas de código reinam no pacote de pacotes de analisadores FxCop.

1. Crie um arquivo de texto. Como exemplo, você pode nomeá-lo *CodeMetricsConfig.txt*.

2. Adicione os limiares desejados ao arquivo de texto no seguinte formato:

   ```txt
   CA1502: 10
   ```

   Neste exemplo, a regra [CA1502](ca1502.md) é configurada para disparar quando a complexidade ciclomática de um método é maior que 10.

3. Na janela **Propriedades** do Visual Studio, ou no arquivo do projeto, marque a ação de compilação do arquivo de configuração como [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Por exemplo:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Calcular comando de menu De métricas de código

Gere métricas de código para um ou todos os seus projetos abertos no IDE usando o menu **Analisar** > **métricas de código de cálculo.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Gerar resultados de métricas de código para uma solução inteira

Você pode gerar resultados de métricas de código para uma solução inteira de qualquer uma das seguintes maneiras:

- Na barra de menu, escolha **Analisar métricas** > **de** > código**para solução**.

- No **Solution Explorer,** clique com o botão direito do mouse na solução e escolha **Calcular Métricas de Código**.

- Na janela **Resultados de métricas de código,** escolha o botão **Calcular métricas de código para solução.**

Os resultados são **gerados** e a janela Resultados de Métricas de Código é exibida. Para visualizar os detalhes dos resultados, expanda a árvore na coluna **Hierarquia.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Gerar resultados de métricas de código para um ou mais projetos

1. No **Solution Explorer,** selecione um ou mais projetos.

1. Na barra de menu, escolha **Analisar** > **métricas** > de código**para projetos selecionados.**

Os resultados são **gerados** e a janela Resultados de Métricas de Código é exibida. Para visualizar os detalhes dos resultados, expanda a árvore na **Hierarquia**.

::: moniker range="vs-2017"

> [!NOTE]
> O **comando Calculate Code Metrics** não funciona para projetos .NET Core e .NET Standard. Para calcular as métricas de código de um projeto .NET Core ou .NET Standard, você pode:
>
> - Calcule as métricas de código da [linha de comando](#command-line-code-metrics) em vez disso
>
> - Upgrade para [visual studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Métricas de código de linha de comando

Você pode gerar dados de métricas de código da linha de comando para projetos C# e Visual Basic para aplicativos .NET Framework, .NET Core e .NET Standard. Para executar métricas de código da linha de comando, instale o [pacote Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) ou crie o [executável Metrics.exe.](#metricsexe)

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Pacote Microsoft.CodeAnalysis.Metrics NuGet

A maneira mais fácil de gerar dados de métricas de código da linha de comando é instalando o pacote [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet. Depois de instalar o pacote, `msbuild /t:Metrics` execute a partir do diretório que contém o arquivo do projeto. Por exemplo:

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

Você pode substituir o nome do `/p:MetricsOutputFile=<filename>`arquivo de saída especificando . Você também pode obter dados de métricas `/p:LEGACY_CODE_METRICS_MODE=true`de código de estilo [legado](#previous-versions) especificando . Por exemplo:

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

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Se você não quiser instalar o pacote NuGet, você pode gerar e usar o *executável Metrics.exe* diretamente. Para gerar o *Executável Metrics.exe:*

1. Clone o repo [dotnet/roslyn-analyzers.](https://github.com/dotnet/roslyn-analyzers)
2. Abrir o Prompt de comando do desenvolvedor para o Visual Studio como administrador.
3. A partir da raiz do repo **roslyn-analyzers,** execute o seguinte comando:`Restore.cmd`
4. Alterar diretório para *src\Tools*.
5. Execute o seguinte comando para construir o projeto **Metrics.csproj:**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Um executável chamado *Metrics.exe* é gerado no diretório *artifacts\bin* sob a raiz do repo.

#### <a name="metricsexe-usage"></a>Uso de metrics.exe

Para executar *Metrics.exe,* forneça um projeto ou solução e um arquivo XML de saída como argumentos. Por exemplo:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modo legado

Você pode optar por criar *Metrics.exe* no *modo legado*. A versão do modo legado da ferramenta gera valores métricos mais próximos do que [as versões mais antigas da ferramenta geraram.](#previous-versions) Além disso, no modo legado, *o Metrics.exe* gera métricas de código para o mesmo conjunto de tipos de método susceptíveis de que as versões anteriores da ferramenta geraram métricas de código para. Por exemplo, ele não gera dados de métricas de código para iniciadores de campo e propriedade. O modo legado é útil para compatibilidade reversa ou se você tiver portões de check-in de código com base em números de métricas de código. O comando para construir *Metrics.exe* no modo legado é:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Para obter mais informações, consulte [Ativar a geração de métricas de código no modo legado](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versões anteriores

::: moniker range=">=vs-2019"
O Visual Studio 2015 incluiu uma ferramenta de métricas de código de linha de comando que também foi chamada *de Metrics.exe*. Esta versão anterior da ferramenta fez uma análise binária, ou seja, uma análise baseada em montagem. A versão mais recente da ferramenta *Metrics.exe* analisa o código-fonte. Como a ferramenta *metrics.exe* mais nova é baseada em código-fonte, os resultados das métricas de código de linha de comando podem ser diferentes daqueles gerados pelo Visual Studio IDE e pelas versões anteriores do *Metrics.exe*. A partir do Visual Studio 2019, o Visual Studio IDE analisa código-fonte como a ferramenta de linha de comando e os resultados devem ser os mesmos.

::: moniker-end
::: moniker range="vs-2017"
O Visual Studio 2015 incluiu uma ferramenta de métricas de código de linha de comando que também foi chamada *de Metrics.exe*. Esta versão anterior da ferramenta fez uma análise binária, ou seja, uma análise baseada em montagem. A nova ferramenta *Metrics.exe* analisa o código-fonte. Como a nova ferramenta *Metrics.exe* é baseada em código-fonte, os resultados das métricas de código de linha de comando são diferentes daqueles gerados pelo Visual Studio IDE e pelas versões anteriores do *Metrics.exe*.
::: moniker-end

A nova ferramenta de métricas de código de linha de comando calcula métricas mesmo na presença de erros de código-fonte, desde que a solução e o projeto possam ser carregados.

#### <a name="metric-value-differences"></a>Diferenças de valor métrica

::: moniker range=">=vs-2019"
Começando no Visual Studio 2019 versão 16.4 e Microsoft.CodeAnalysis.Metics (2.9.5), `SourceLines` e `ExecutableLines` substitua a métrica anterior. `LinesOfCode` Para obter descrições das novas métricas, consulte [Valores de métricas](../code-quality/code-metrics-values.md)de código . A `LinesOfCode` métrica está disponível no modo legado.
::: moniker-end
::: moniker range="vs-2017"
A `LinesOfCode` métrica é mais precisa e confiável na nova ferramenta de métricas de código de linha de comando. Ele é independente de quaisquer diferenças de codegen e não muda quando o conjunto de ferramentas ou o tempo de execução muda. A nova ferramenta conta linhas de código reais, incluindo linhas em branco e comentários.
::: moniker-end

Outras métricas `CyclomaticComplexity` `MaintainabilityIndex` como e usar as mesmas fórmulas das versões anteriores `IOperations` do *Metrics.exe,* mas a nova ferramenta conta o número de instruções (instruções de origem lógica) em vez de instruções de linguagem intermediária (IL). Os números serão ligeiramente diferentes dos gerados pelo Visual Studio IDE e pelas versões anteriores do *Metrics.exe*.

## <a name="see-also"></a>Confira também

- [Use a janela Resultados de Métricas de Código](../code-quality/working-with-code-metrics-data.md)
- [Valores de métricas de código](../code-quality/code-metrics-values.md)
