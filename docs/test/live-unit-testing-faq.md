---
title: Perguntas frequentes sobre o Live Unit Testing
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: gewarren
ms.author: gewarren
ms.workload:
- dotnet
ms.openlocfilehash: 545c8974e3d0dea196a6168db03586a37d15ed72
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262296"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Perguntas frequentes sobre o Live Unit Testing

## <a name="supported-frameworks"></a>Estruturas com suporte

**Quais são as estruturas de teste compatíveis com o Live Unit Testing e quais são as versões mínimas compatíveis?**

O Live Unit Testing funciona com as três estruturas de teste de unidade populares listadas na tabela a seguir. A versão mínima com suporte de seus adaptadores e suas estruturas também é listada na tabela. As estruturas de teste de unidade estão disponíveis em NuGet.org.

|Estrutura de teste  |Versão mínima do Adaptador do Visual Studio  |Versão mínima da Estrutura  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio versão 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter versão 3.7.0 |NUnit versão 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Se você tiver projetos de teste com base em MSTest mais antigos que referenciem `Microsoft.VisualStudio.QualityTools.UnitTestFramework` e não quiser migrar para os pacotes mais recentes do MSTest NuGet, atualize para o Visual Studio 2019 ou Visual Studio 2017.

Em alguns casos, talvez seja necessário restaurar explicitamente os pacotes NuGet referenciados pelos projetos na solução para que o Live Unit Testing funcione. Você pode restaurar os pacotes fazendo uma compilação explícita da solução (selecione **compilar** > **Recompilar solução** no menu do Visual Studio de nível superior) ou clicando com o botão direito do mouse na solução e selecionando **restaurar pacotes NuGet** antes de habilitar o teste de unidade de vida.

## <a name="net-core-support"></a>Suporte do .NET Core

**O Live Unit Testing funciona com o .NET Core?**

Sim. O Live Unit Testing funciona com o .NET Core e .NET Framework.

## <a name="configuration"></a>Configuração

**Por que o Live Unit Testing não funciona ao ser ligado?**

A janela de saída (quando a lista suspensa Live Unit Testing está selecionada) deve informar por que Live Unit Testing não está funcionando. O Live Unit Testing poderá não funcionar por um dos seguintes motivos:

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

**Por que o Live Unit Testing mostra uma cobertura incorreta depois de atualizar o adaptador de teste referenciado nos Projetos do Visual Studio para a versão compatível?**

- Se vários projetos na solução referenciarem o pacote do adaptador de teste NuGet, cada um deles deverá ser atualizado para a versão com suporte.

- Verifique também se o arquivo *.props* do MSBuild importado do pacote do adaptador de teste foi atualizado corretamente. Verifique a versão e o caminho da importação do pacote NuGet, que geralmente podem ser encontrados próximo à parte superior do arquivo de projeto, da seguinte forma:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Builds personalizados

**Posso personalizar meus builds do Live Unit Testing?**

Se a solução exigir etapas personalizadas de build para instrumentação (Live Unit Testing) que não são necessárias para o build não instrumentado "normal", você poderá adicionar o código ao projeto ou arquivos *.targets* que verificam a propriedade `BuildingForLiveUnitTesting` e executam etapas de pré/pós-build personalizadas. Também é possível optar por remover algumas etapas de build (como publicar ou gerar pacotes) ou adicionar etapas de build (como copiar pré-requisitos) a um build do Live Unit Testing baseado na propriedade desse projeto. A personalização do build com base nessa propriedade não altera o build normal de nenhum modo e só afeta os builds do Live Unit Testing.

Por exemplo, pode haver um destino que produz pacotes NuGet durante um build normal. Provavelmente, você não desejará que os pacotes NuGet sejam gerados após cada edição feita. Portanto, é possível desabilitar esse destino no build do Live Unit Testing fazendo algo semelhante ao seguinte:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-or-outdir"></a>Mensagens de erro com \<OutputPath > ou \<OutDir >

**Por que recebo este erro quando o Live Unit Testing tenta criar minha solução: “... parece definir `<OutputPath>` ou `<OutDir>` incondicionalmente. O Live Unit Testing não executará testes do assembly de saída”?**

Você pode receber esse erro se o processo de build da solução substitui `<OutputPath>` ou `<OutDir>` incondicionalmente e, portanto, ele não é um subdiretório de `<BaseOutputPath>`. Nesses casos, o Live Unit Testing não funcionará, pois ele também substitui esses valores, a fim de garantir que os artefatos de build sejam soltos em uma pasta em `<BaseOutputPath>`. Se precisar substituir a localização em que você deseja que os artefatos de build sejam soltos em um build normal, substitua o `<OutputPath>` condicionalmente com base em `<BaseOutputPath>`.

Por exemplo, se o build substituir o `<OutputPath>`, conforme mostrado abaixo:

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

## <a name="build-artifact-location"></a>Localização do artefato de compilação

**Quero que os artefatos de um build do Live Unit Testing sejam encaminhados para uma localização específica em vez da localização padrão na pasta *.vs*. Como fazer para alterar isso?**

Defina a variável de ambiente em nível de usuário `LiveUnitTesting_BuildRoot` com o caminho no qual você deseja que os artefatos de build do Live Unit Testing sejam soltos. 

## <a name="test-explorer-versus-live-unit-testing"></a>Gerenciador de testes versus Live Unit Testing

**Qual a diferença entre a execução de testes na janela do Gerenciador de Testes e no Live Unit Testing?**

Há várias diferenças:

- A execução ou a depuração de testes na janela **Gerenciador de Testes** executa binários regulares, enquanto o Live Unit Testing executa binários instrumentados. Se você desejar depurar binários instrumentados, a adição de uma chamada de método [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) ao método de teste fará com que o depurador seja iniciado sempre que o método for executado (incluindo quando ele for executado pelo Live Unit Testing). Em seguida, será possível anexar e depurar o binário instrumentado. No entanto, esperamos que a instrumentação seja transparente para você na maioria dos cenários de usuário e que você não precise depurar binários instrumentados.

- O Live Unit Testing não cria um domínio do aplicativo para executar testes, mas os testes executados por meio da janela **Gerenciador de Testes** criam um domínio do aplicativo.

- O Live Unit Testing executa testes em cada assembly de teste sequencialmente. No **Gerenciador de testes**, você pode optar por executar vários testes em paralelo.

- A descoberta e a execução de testes no Live Unit Testing usam a versão 2 do `TestPlatform`, enquanto a janela **Gerenciador de Testes** usa a versão 1. No entanto, você não observará nenhuma diferença na maioria dos casos.

- O **Gerenciador de testes** executa testes em um STA (single-threaded apartment) por padrão, enquanto Live Unit Testing executa testes em um MTA (multi-threaded apartment). Para executar testes do MSTest no STA no Live Unit Testing, decore o método de teste ou a classe recipiente com o atributo `<STATestMethod>` ou `<STATestClass>` que pode ser encontrado no pacote NuGet `MSTest.STAExtensions 1.0.3-beta`. Para o NUnit, decore o método de teste com o atributo `<RequiresThread(ApartmentState.STA)>` e para o xUnit, com o atributo `<STAFact>`.

## <a name="exclude-tests"></a>Excluir testes

**Como faço para excluir testes de participação do Live Unit Testing?**

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

**Por que o Live Unit Testing continua compilando minha solução o tempo inteiro, mesmo quando não estou fazendo edições?**

Sua solução pode ser criada mesmo se você não estiver fazendo edições se o processo de compilação gerar o código-fonte que faz parte da solução em si e os arquivos de destino da compilação não tiverem entradas e saídas apropriadas especificadas. Os destinos devem receber uma lista de entradas e saídas para que o MSBuild possa executar as verificações atualizadas apropriadas e determinar se um novo build é necessário.

O Live Unit Testing inicia um build sempre que detecta uma alteração nos arquivos de origem. Como a compilação da solução gera arquivos de origem, Live Unit Testing entra em um loop de compilação infinito. Se, no entanto, as entradas e saídas do destino forem verificadas quando Live Unit Testing iniciar a segunda compilação (depois de detectar os arquivos de origem gerados recentemente a partir da compilação anterior), ele interromperá o loop de compilação, pois as verificações de entradas e saídas indicam que Tudo está atualizado.

## <a name="editor-icons"></a>Ícones do editor

**Por que não consigo ver nenhum ícone no editor, embora o Live Unit Testing pareça estar executando os testes de acordo com as mensagens na janela de Saída?**

Talvez você não veja ícones no editor se os assemblies que o Live Unit Testing está operando não estão instrumentados por algum motivo. Por exemplo, o Live Unit Testing não é compatível com projetos que definem `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Nesse caso, o processo de build precisa ser atualizado para remover essa configuração ou alterá-la para `true`, a fim de que o Live Unit Testing funcione. 

## <a name="capture-logs"></a>Coletar logs

**Como faço para coletar logs mais detalhados de relatórios de registros de bugs?**

É possível fazer várias coisas para coletar logs mais detalhados:

- Acesse **Ferramentas** > **Opções** > **Live Unit Testing** e altere a opção de log para **Detalhado**. O log detalhado faz com que logs mais detalhados sejam mostrados na janela de **Saída**.

- Defina a variável de ambiente do usuário `LiveUnitTesting_BuildLog` com o nome do arquivo que você deseja usar para capturar o log do MSBuild. Em seguida, as mensagens de log detalhado do MSBuild de builds do Live Unit Testing podem ser recuperadas desse arquivo.

- Defina a variável de ambiente de usuário `LiveUnitTesting_TestPlatformLog` como `1` para capturar o log da Plataforma de Teste. Em seguida, as mensagens de log da Plataforma de Teste das execuções do Live Unit Testing poderão ser recuperadas de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Crie uma variável de ambiente em nível de usuário chamada `VS_UTE_DIAGNOSTICS` e defina-a como 1 (ou qualquer valor) e reinicie o Visual Studio. Agora você verá muitos logs na guia **Saída – Testes** do Visual Studio.

## <a name="see-also"></a>Consulte também

- [Teste de Unidade Dinâmica](live-unit-testing.md)
