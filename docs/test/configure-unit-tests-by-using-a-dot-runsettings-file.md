---
title: Configurar testes de unidade com um arquivo .runsettings
ms.date: 06/14/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4194a392eee1d5c9beaa0640f4006d1f01ebbace
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262320"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurar testes de unidade usando um *.runsettings*

Os testes de unidade no Visual Studio podem ser configurados com um arquivo *.runsettings*. Por exemplo, é possível alterar a versão do .NET na qual os testes são executados, o diretório para os resultados de teste ou os dados coletados durante uma execução de teste.

Arquivos de configurações de execução são opcionais. Se você não precisar de nenhuma configuração especial, não será necessário ter um arquivo *.runsettings*. Um uso comum de um arquivo *.runsettings* é personalizar a [análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Especificar um arquivo de configurações de execução

Os arquivos de configurações de execução podem ser usados para configurar os testes executados na [linha de comando](vstest-console-options.md), no IDE ou em um [fluxo de trabalho de build](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) usando o Azure Test Plans ou o TFS (Team Foundation Server).

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Para especificar um arquivo de configurações de execução no IDE, selecione **Teste** > **Configurações do Teste** > **Selecionar Arquivo de Configurações do Teste** e, em seguida, selecione o arquivo *.runsettings*.

![Selecionar o menu do arquivo de configurações do teste no Visual Studio 2017](media/select-test-settings-file.png)

O arquivo será exibido no menu de Configurações do Teste e você poderá marcá-lo ou desmarcá-lo. Quando estiver marcado, o arquivo de configurações de execução se aplicará sempre que você selecionar **Analisar Cobertura de Código**.

::: moniker-end

::: moniker range=">=vs-2019"

Para especificar um arquivo de configurações de execução no IDE, selecione **testar** > **Selecione arquivo de configurações**. Navegue até o arquivo *.runsettings* e selecione-o.

![Selecionar o menu do arquivo de configurações do teste no Visual Studio 2019](media/vs-2019/select-settings-file.png)

O arquivo aparece no menu teste e você pode selecioná-lo ou desselecioná-lo. Quando estiver marcado, o arquivo de configurações de execução se aplicará sempre que você selecionar **Analisar Cobertura de Código**.

::: moniker-end

### <a name="command-line"></a>Linha de comando

Para executar testes na linha de comando, use o *vstest.console.exe* e especifique o arquivo de configurações usando o parâmetro **/Settings**.

1. Inicie o Prompt de Comando do Desenvolvedor do Visual Studio:

   ::: moniker range="vs-2017"

   No menu **Iniciar** do Windows, escolha **Visual Studio 2017** > **Prompt de Comando do Desenvolvedor para VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   No menu **Iniciar** do Windows, escolha **Visual Studio 2019** > **Prompt de Comando do Desenvolvedor para VS 2019**.

   ::: moniker-end

2. Insira um comando semelhante a:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   ou

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Para obter mais informações, consulte [Opções de linha de comando de VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Personalizar testes

Para personalizar os testes usando um arquivo *.runsettings*, siga estas etapas:

1. Adicione um arquivo XML à solução do Visual Studio e salve-o como *test.runsettings*.

   > [!TIP]
   > O nome do arquivo não é importante, desde que você use a extensão *.runsettings*.

2. Substitua o conteúdo do arquivo pelo XML do exemplo a seguir e personalize-o conforme o necessário.

::: moniker range="vs-2017"

3. No menu **Testar**, escolha **Configurações de Teste** > **Selecionar Arquivo de Configurações de Teste**. Procure o arquivo *.runsettings* que você criou e, em seguida, selecione **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Para selecionar o arquivo de configurações de execução, escolha **testar** > **Selecionar arquivo de configurações**. Procure o arquivo *.runsettings* que você criou e, em seguida, selecione **OK**.

::: moniker-end

   > [!TIP]
   > Crie mais de um arquivo *.runsettings* na solução e selecione um como o arquivo ativo de configurações do teste, conforme necessário.

## <a name="example-runsettings-file"></a>Arquivo *.runsettings* de exemplo

O XML a seguir mostra o conteúdo de um arquivo *.runsettings* típico. Cada elemento do arquivo é opcional, porque tem um valor padrão.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>
            
          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Elementos de um arquivo *.runsettings*

As seções a seguir detalham os elementos de um arquivo *.runsettings*.

### <a name="run-configuration"></a>Configuração de execução

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

O elemento **RunConfiguration** pode incluir os seguintes elementos:

|Nó|Padrão|Valores|
|-|-|-|
|**ResultsDirectory**||O diretório no qual os resultados do teste são colocados.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` para fontes do .NET Core, `FrameworkUap10` para fontes baseadas no UWP, `Framework45` para o .NET Framework 4.5 e posterior, `Framework40` para o .NET Framework 4.0 e `Framework35` para o .NET Framework 3.5.<br /><br />Essa configuração especifica a versão da estrutura de teste de unidade usada para descobrir e executar os testes. Pode ser diferente da versão da plataforma .NET especificada nas propriedades de compilação do projeto de teste de unidade.<br /><br />Se você omitir o elemento `TargetFrameworkVersion` a partir do arquivo *.runsettings*, a plataforma determinará automaticamente a versão da estrutura com base nos binários compilados.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Um ou mais caminhos para o diretório no qual os TestAdapters estão localizados|
|**MaxCpuCount**|1|Essa configuração controla o grau de execução de teste paralela ao executar testes de unidade usando os núcleos disponíveis no computador. O mecanismo de execução de testes inicia como um processo distinto em cada núcleo disponível e fornece um contêiner para cada núcleo com testes a serem executados. Um contêiner pode ser um assembly, uma DLL ou um artefato relevante. O contêiner do teste está agendando a unidade. Em cada contêiner, os testes são executados de acordo com a estrutura de teste. Se houver muitos contêineres, à medida que os processos concluírem a execução dos testes em um contêiner, eles passarão para o próximo contêiner disponível.<br /><br />MaxCpuCount pode ser:<br /><br />n, em que 1 <= n <= número de núcleos: até n processos são iniciados<br /><br />n, em que n = qualquer outro valor: o número de processos iniciados pode ter até o número de núcleos disponíveis|
|**TestSessionTimeout**||Permite que os usuários finalizem uma sessão de teste quando ele exceder o tempo limite determinado. Definir um tempo limite assegura que os recursos serão restritos e as sessões de teste serão restritas a um período de tempo. Essa configuração está disponível no **Visual Studio 2017 versão 15.5** e posterior.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptadores de dados de diagnóstico (coletores de dados)

O elemento **DataCollectors** especifica as configurações de adaptadores de dados de diagnóstico. Os adaptadores de dados de diagnóstico coletam informações adicionais sobre o ambiente e o aplicativo em teste. Cada adaptador tem configurações padrão e você só precisará fornecer configurações caso não deseje usar os padrões.

#### <a name="code-coverage-adapter"></a>Adaptador de cobertura de código

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

O coletor de dados de cobertura de código cria um log das partes do código do aplicativo que foram utilizadas no teste. Para obter mais informações sobre como personalizar as configurações de cobertura de código, confira [Personalizar a análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Coletor de dados de vídeo

O coletor de dados de vídeo captura uma gravação de tela quando os testes são executados. A gravação é útil para solucionar problemas de testes de interface do usuário. O coletor de dados de vídeo está disponível no **Visual Studio 2017 versão 15.5** e posterior.

Para personalizar qualquer outro tipo de adaptador de dados de diagnóstico, use um [arquivo de configurações do teste](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Os parâmetros de execução de teste fornecem uma maneira de definir variáveis e valores que estão disponíveis para os testes em tempo de execução. Acesse os parâmetros usando a propriedade <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Para usar parâmetros de execução de teste, adicione um campo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> particular e uma propriedade <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pública à classe de teste.

### <a name="mstest-run-settings"></a>Configurações de execução do MSTest

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Essas configurações são específicas para o adaptador de teste que executa os métodos de teste que têm o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>.

|Configuração|Padrão|Valores|
|-|-|-|
|**ForcedLegacyMode**|false|No Visual Studio 2012, o adaptador MSTest foi otimizado para torná-lo mais rápido e mais escalonável. Alguns comportamentos, como a ordem em que os testes são executados, não podem ser exatamente iguais aos de edições anteriores do Visual Studio. Defina esse valor como **true** para usar o adaptador de teste mais antigo.<br /><br />Por exemplo, você poderá usar essa configuração se tiver um arquivo *app.config* especificado para um teste de unidade.<br /><br />Recomendamos que você considere refatorar seus testes para permitir o uso do adaptador mais recente.|
|**IgnoreTestImpact**|false|O recurso de impacto de teste prioriza os testes que são afetados pelas alterações recentes, quando executados no MSTest ou no Microsoft Test Manager. Essa configuração desativa o recurso. Para obter mais informações, confira [Quais testes devem ser executados desde um build anterior](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Especifique um arquivo de configurações do teste para usar com o adaptador MSTest aqui. Você também pode especificar um arquivo de configurações do teste [no menu de configurações](#ide).<br /><br />Se você especificar esse valor, também será necessário definir o **ForcedlegacyMode** como **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Após a execução do teste ser concluída, o MSTest será fechado. Qualquer processo iniciado como parte do teste também será eliminado. Caso deseje manter o executor de teste ativo, defina o valor como **true**. Por exemplo, você pode usar essa configuração para manter o navegador em execução entre os testes de IU codificados.|
|**DeploymentEnabled**|true|Se você definir esse valor como **false**, os itens de implantação especificados no método de teste não serão copiados para o diretório de implantação.|
|**CaptureTraceOutput**|true|Grave no rastreamento de depuração por meio do método de teste usando <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Para reter o diretório de implantação após uma execução de teste, defina esse valor como **false**.|
|**MapInconclusiveToFailed**|false|Se um teste for concluído com um status inconclusivo, ele será mapeado para o status Ignorado no **Gerenciador de Testes**. Caso deseje que os testes inconclusivos sejam mostrados como com falha, defina esse valor como **true**.|
|**InProcMode**|false|Caso deseje que os testes sejam executados no mesmo processo do adaptador MSTest, defina esse valor como **true**. Essa configuração fornece um ganho menor de desempenho. No entanto, se um teste for encerrado com uma exceção, os testes restantes não serão executados.|
|**AssemblyResolution**|false|É possível especificar caminhos para outros assemblies ao localizar e executar testes de unidade. Por exemplo, use esses caminhos para assemblies de dependência que não estão no mesmo diretório do assembly de teste. Para especificar um caminho, use um elemento **Caminho do Diretório**. Os caminhos podem incluir variáveis de ambiente.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Consulte também

- [Configurar uma execução de teste](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Personalizar a análise de cobertura de código](../test/customizing-code-coverage-analysis.md)
- [Tarefa de teste do Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
