---
title: Perguntas frequentes sobre o Live Unit Testing
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: ba231e6c203197518b75a7a8c0592f01bba4ffe9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591535"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Perguntas frequentes sobre o Live Unit Testing

## <a name="supported-frameworks"></a>Estruturas com suporte

**Quais estruturas de teste são compatíveis com o Live Unit Testing e quais são as versões mínimas compatíveis?**

O Live Unit Testing funciona com as três estruturas de teste de unidade populares listadas na tabela a seguir. A versão mínima com suporte de seus adaptadores e suas estruturas também é listada na tabela. As estruturas de teste de unidade estão disponíveis em NuGet.org.

|Estrutura de teste  |Versão mínima do Adaptador do Visual Studio  |Versão mínima da Estrutura  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio versão 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter versão 3.7.0 |NUnit versão 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Se você tem projetos de teste `Microsoft.VisualStudio.QualityTools.UnitTestFramework` baseados no MSTest mais antigos que fazem referência e não deseja passar para os pacotes mais novos do MSTest NuGet, atualize para o Visual Studio 2019 ou o Visual Studio 2017.

Em alguns casos, talvez seja necessário restaurar explicitamente os pacotes NuGet referenciados pelos projetos na solução para que o Live Unit Testing funcione. Você pode restaurar os pacotes fazendo uma compilação explícita da solução (selecione **Build** > **Rebuild Solution** no menu de alto nível do Visual Studio) ou clicando com o botão direito do mouse na solução e selecionando Restaurar **pacotes NuGet** antes de ativar o teste da unidade viva.

## <a name="net-core-support"></a>Suporte do .NET Core

**O Live Unit Testing funciona com o .NET Core?**

Sim. O Live Unit Testing funciona com o .NET Core e .NET Framework.

## <a name="configuration"></a>Configuração

**Por que o Live Unit Testing não funciona ao ser ligado?**

A janela Saída (quando a lista de testes da unidade viva estiver selecionada) deve dizer por que o teste da unidade ao vivo não está funcionando. O Live Unit Testing poderá não funcionar por um dos seguintes motivos:

- Se os pacotes NuGet referenciados pelos projetos na solução não tiverem sido restaurados, o Live Unit Testing não funcionará. Fazer uma compilação explícita da solução ou restaurar os pacotes NuGet na solução antes de ativar o Live Unit Testing deverá resolver esse problema.

- Se estiver usando testes baseados no MSTest nos projetos, lembre-se de remover a referência a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` e adicionar referências aos últimos pacotes NuGet do MSTest: `MSTest.TestAdapter` (uma versão mínima de 1.1.11 é necessária) e `MSTest.TestFramework` (uma versão mínima de 1.1.11 é necessária). Para obter mais informações, confira a seção "Estruturas de teste compatíveis" do artigo [Usar o Live Unit Testing no Visual Studio](live-unit-testing.md#supported-test-frameworks).

- No mínimo, um projeto na solução deve ter uma referência ao NuGet ou uma referência direta à estrutura de teste do xUnit, NUnit ou MSTest. Esse projeto também deve referenciar um pacote NuGet de adaptadores de teste do Visual Studio correspondente. O adaptador de teste do Visual Studio também pode ser referenciado por meio de um arquivo *.runsettings*. O arquivo *.runsettings* precisa ter uma entrada como o seguinte exemplo:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Cobertura incorreta após a atualização

**Por que o Live Unit Testing mostra uma cobertura incorreta depois de atualizar o adaptador de teste referenciado nos Projetos do Visual Studio para a versão com suporte?**

- Se vários projetos na solução referenciarem o pacote do adaptador de teste NuGet, cada um deles deverá ser atualizado para a versão com suporte.

- Certifique-se de que o arquivo MSBuild *.props* importado do pacote de adaptador de teste também esteja corretamente atualizado. Verifique a versão e o caminho da importação do pacote NuGet, que geralmente podem ser encontrados próximo à parte superior do arquivo de projeto, da seguinte forma:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Builds personalizados

**Posso personalizar meus builds do Live Unit Testing?**

Se a solução exigir etapas personalizadas para serem construídas para instrumentação (Testes de unidade ao vivo) que não sejam necessárias para `BuildingForLiveUnitTesting` a compilação "regular" não instrumentada, então você pode adicionar código ao seu projeto ou arquivos .targets que verificam a propriedade e executam *etapas personalizadas* de compilação pré/pós. Também é possível optar por remover algumas etapas de build (como publicar ou gerar pacotes) ou adicionar etapas de build (como copiar pré-requisitos) a um build do Live Unit Testing baseado na propriedade desse projeto. A personalização do build com base nessa propriedade não altera o build normal de nenhum modo e só afeta os builds do Live Unit Testing.

Por exemplo, pode haver um destino que produz pacotes NuGet durante um build normal. Provavelmente, você não desejará que os pacotes NuGet sejam gerados após cada edição feita. Portanto, é possível desabilitar esse destino no build do Live Unit Testing fazendo algo semelhante ao seguinte:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Mensagens de \<erro com \<> do \<OutputPath, outdir> ouPathPath>

**Por que eu recebo o seguinte erro quando o Live Unit Testing tenta construir minha solução: "... parece definir `<OutputPath>` incondicionalmente ou `<OutDir>`. O Teste da Unidade Viva não executará testes a partir do conjunto de saída"?**

Você pode obter esse erro se o processo de compilação da sua solução tiver uma lógica personalizada que especifica onde binários devem ser gerados. Por padrão, a localização de `<OutputPath>`seus `<OutDir>` `<IntermediateOutputPath>` binários `<BaseOutputPath>` `<BaseIntermediateOutputPath>`depende , ou bem como ou .

O Live Unit Testing substitui essas variáveis para garantir que os artefatos de construção sejam descartados para uma pasta de artefatos de teste de unidade viva e falhará se o processo de compilação também anular essas variáveis.

Existem duas abordagens principais para fazer com que o Live Unit Testing seja construído com sucesso. Para facilitar as configurações de compilação, você pode basear seus caminhos de saída em `<BaseIntermediateOutputPath>`. Para configurações mais complexas, você `<LiveUnitTestingBuildRootPath>`pode basear seus caminhos de saída .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Substituindo `<OutputPath>` / `<IntermediateOutputPath>` condicionalmente `<BaseOutputPath>` / `<BaseIntermediateOutputPath>`com base em .

> [!NOTE]
> Para usar essa abordagem, cada projeto precisa ser capaz de construir independentemente um do outro. Não tenha um projeto de referência de artefatos de outro projeto durante a construção. Não tenha um projeto de carga dinâmica de conjuntos de `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`outro projeto durante o tempo de execução (por exemplo, chamada ).

Durante a compilação, o Live `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` Unit Testing substitui automaticamente as variáveis para direcionar a pasta de artefatos de teste da unidade viva.

Por exemplo, se o build substituir o <OutputPath>, conforme mostrado abaixo:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

em seguida, substitua-o pelo seguinte XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Isso garante que `<OutputPath>` reside na pasta `<BaseOutputPath>`.

Não substitua `<OutDir>` diretamente no processo de build; em vez disso, substitua `<OutputPath>` para soltar os artefatos de build em uma localização específica.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Substituindo suas propriedades `<LiveUnitTestingBuildRootPath>` com base na propriedade.

> [!NOTE]
> Nesta abordagem, você precisa ter cuidado com arquivos adicionados a pasta de artefatos que não são gerados durante a compilação. O exemplo abaixo mostra o que fazer ao colocar a pasta de pacotes artefatos. Como o conteúdo desta pasta não é gerado durante a compilação, a propriedade MSBuild **não deve ser alterada**.

Durante uma compilação de `<LiveUnitTestingBuildRootPath>` testes de unidade ao vivo, a propriedade é definida para a localização da pasta de artefatos de teste da unidade viva.

Por exemplo, suponha que seu projeto tenha a estrutura mostrada aqui.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Durante a compilação de `<LiveUnitTestingBuildRootPath>` testes da unidade viva, `.vs\...\lut\0\b`a propriedade é definida para o caminho completo de . Se o projeto `<ArtifactsRoot>` definir a propriedade que mapeia a solução dir, você poderá atualizar o projeto MSBuild da seguinte forma:

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Construir localização do artefato

**Quero que os artefatos de uma compilação de teste de unidade ao vivo sejam para um local específico em vez do local padrão a pasta *.vs.* Como posso mudar isso?**

Defina a variável de ambiente em nível de usuário `LiveUnitTesting_BuildRoot` com o caminho no qual você deseja que os artefatos de build do Live Unit Testing sejam soltos. 

## <a name="test-explorer-versus-live-unit-testing"></a>Teste Explorer versus Teste de Unidade Ao Vivo

**Qual a diferença entre a execução de testes na janela Gerenciador de Testes e a execução de testes no Live Unit Testing?**

Há várias diferenças:

- Os testes de execução ou depuração da janela **Do Explorador** de Teste executam binários regulares, enquanto o Live Unit Testing executa binários instrumentados. Se você quiser depurar binários instrumentados, adicionar uma chamada de método [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) no método de teste faz com que o depurador seja lançado sempre que esse método for executado (inclusive quando for executado pelo Live Unit Testing), e você poderá anexar e depurar o binário instrumentado. No entanto, esperamos que a instrumentação seja transparente para você na maioria dos cenários de usuário e que você não precise depurar binários instrumentados.

- O Live Unit Testing não cria um novo domínio de aplicativo para executar testes, mas os testes executados a partir da janela **Do Explorador** de Teste criam um novo domínio de aplicativo.

- O Live Unit Testing executa testes em cada assembly de teste sequencialmente. No **Test Explorer,** você pode optar por executar vários testes em paralelo.

- **O Test Explorer** executa testes em um apartamento de um único rosca (STA) por padrão, enquanto o Live Unit Testing executa testes em um apartamento de vários rosca (MTA). Para executar testes do MSTest no STA no Live Unit Testing, decore o método de teste ou a classe recipiente com o atributo `<STATestMethod>` ou `<STATestClass>` que pode ser encontrado no pacote NuGet `MSTest.STAExtensions 1.0.3-beta`. Para o NUnit, decore o método de teste com o atributo `<RequiresThread(ApartmentState.STA)>` e para o xUnit, com o atributo `<STAFact>`.

## <a name="exclude-tests"></a>Excluir testes

**Como fazer para excluir testes de fazer parte do Live Unit Testing?**

Confira a seção "Incluir e excluir projetos e métodos de teste" do artigo [Usar o Live Unit Testing no Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) para obter a configuração específica do usuário. É útil incluir ou excluir testes quando você deseja executar um conjunto específico de testes em uma sessão de edição específica ou para persistir suas próprias preferências pessoais.

Para configurações específicas da solução, você pode aplicar o atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> programaticamente para excluir métodos, propriedades, classes ou estruturas de serem instrumentados pelo by Live Unit Testing. Além disso, também é possível definir a propriedade `<ExcludeFromCodeCoverage>` como `true` no arquivo de projeto para excluir todo o projeto de ser instrumentado. O Live Unit Testing ainda executará os testes que não foram instrumentados, mas sua cobertura não será visualizada.

Verifique também se `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` foi carregado no domínio do aplicativo atual e desabilite testes com base no motivo. Por exemplo, você pode fazer algo semelhante ao seguinte com o xUnit:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Cabeçalhos do Win32 PE

**Por que os cabeçalhos do Win32 PE são diferentes em assemblies instrumentados compilados pelo Live Unit Testing?**

Esse problema foi corrigido e não existe no Visual Studio 2017 versão 15.3 e posterior.

Para versões mais antigas do Visual Studio 2017, há um bug conhecido que pode resultar na falha dos builds do Live Unit Testing em inserir os seguintes dados de Cabeçalho do Win32 PE:

- Versão de Arquivo (especificada por @System.Reflection.AssemblyFileVersionAttribute no código).

- Ícone do Win32 (especificado por `/win32icon:` na linha de comando).

- Manifesto do Win32 (especificado por `/win32manifest:` na linha de comando).

Os testes que dependem desses valores poderão falhar quando executados pelo Live Unit Testing.

::: moniker-end

## <a name="continuous-builds"></a>Builds contínuos

**Por que o Live Unit Testing continua compilando minha solução em todos os momentos, mesmo quando não estou fazendo nenhuma edição?**

Sua solução pode ser construída mesmo se você não estiver fazendo edições se o processo de compilação gerar código-fonte que faz parte da solução em si, e seus arquivos de destino de compilação não têm entradas e saídas apropriadas especificadas. Os destinos devem receber uma lista de entradas e saídas para que o MSBuild possa executar as verificações atualizadas apropriadas e determinar se um novo build é necessário.

O Live Unit Testing inicia um build sempre que detecta uma alteração nos arquivos de origem. Como a compilação da sua solução gera arquivos de origem, o Live Unit Testing entra em um loop de compilação infinito. Se, no entanto, as entradas e saídas do destino forem verificadas quando o Live Unit Testing iniciar a segunda compilação (depois de detectar os arquivos de origem recém-gerados da compilação anterior), ele se rompe do loop de compilação porque as entradas e saídas indicam que tudo está atualizado.

## <a name="editor-icons"></a>Ícones do editor

**Por que não vejo nenhum ícone no editor, embora o Live Unit Testing pareça estar executando os testes com base nas mensagens na janela Saída?**

Talvez você não veja ícones no editor se os assemblies que o Live Unit Testing está operando não estão instrumentados por algum motivo. Por exemplo, o Live Unit Testing não é compatível com projetos que definem `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Nesse caso, o processo de build precisa ser atualizado para remover essa configuração ou alterá-la para `true`, a fim de que o Live Unit Testing funcione. 

## <a name="capture-logs"></a>Coletar logs

**Como fazer para coletar logs mais detalhados de relatórios de bugs de arquivo?**

É possível fazer várias coisas para coletar logs mais detalhados:

- Vá para **Ferramentas** > **Opções De** > **Teste de Unidade Ao Vivo** e altere a opção de registro para **Verbose**. O log detalhado faz com que logs mais detalhados sejam mostrados na janela de **Saída**.

- Defina a variável de ambiente do usuário `LiveUnitTesting_BuildLog` com o nome do arquivo que você deseja usar para capturar o log do MSBuild. Em seguida, as mensagens de log detalhado do MSBuild de builds do Live Unit Testing podem ser recuperadas desse arquivo.

- Defina a variável de ambiente de usuário `LiveUnitTesting_TestPlatformLog` como `1` para capturar o log da Plataforma de Teste. Em seguida, as mensagens de log da Plataforma de Teste das execuções do Live Unit Testing poderão ser recuperadas de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Crie uma variável de ambiente em nível de usuário chamada `VS_UTE_DIAGNOSTICS` e defina-a como 1 (ou qualquer valor) e reinicie o Visual Studio. Agora você deve ver muitos logins na guia **Saída - Testes** no Visual Studio.

## <a name="see-also"></a>Confira também

- [Live Unit Testing](live-unit-testing.md)
