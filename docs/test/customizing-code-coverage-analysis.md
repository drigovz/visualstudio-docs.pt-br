---
title: Personalizando análise de cobertura de código
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bce7a6b9369f33e6fa5248821f58d9903172415c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918645"
---
# <a name="customize-code-coverage-analysis"></a>Personalizar a análise de cobertura de código

Por padrão, a cobertura de código analisa todos os assemblies de solução que são carregados durante os testes de unidade. Recomendamos que esse comportamento padrão seja mantido, pois geralmente ele funciona bem. Para obter mais informações, confira [Usar a cobertura de código para determinar quanto do código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Para excluir o código de teste dos resultados da cobertura de código e incluir apenas o código do aplicativo, adicione o atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> à classe de teste.

Para incluir os assemblies que não fazem parte da solução, obtenha os arquivos *.pdb* desses assemblies e copia-os na mesma pasta que os arquivos *.dll* do assembly.

## <a name="run-settings-file"></a>Arquivo de configurações de execução

O [arquivo de configurações](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) em execução é o arquivo de configuração usado pelas ferramentas de teste unitárias. As configurações avançadas de cobertura de código são especificadas em um arquivo *.runsettings.*

Para personalizar a cobertura de código, siga estas etapas:

1. Adicione um arquivo de configurações de execução à sua solução. No **Solution Explorer,** no menu de atalho da sua solução, escolha **Adicionar** > **novo item**e selecione **Arquivo XML**. Salve o arquivo com um nome como *CodeCoverage.runsettings*.

2. Adicione o conteúdo do arquivo de exemplo no final deste artigo e personalize-o de acordo com suas necessidades, conforme descrito nas seções a seguir.

::: moniker range="vs-2017"

3. Para selecionar o arquivo de configurações de execução, no menu **Testar**, escolha **Testar Configurações** > **Selecionar Arquivo de Configurações do Teste**. Para especificar um arquivo de configurações de execução para executar testes na linha de comando, confira [Configurar testes de unidade](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Para selecionar o arquivo 'executar configurações', no menu **Teste,** escolha **Selecionar Arquivo de configurações**. Para especificar um arquivo de configurações de execução para executar testes na linha de comando, confira [Configurar testes de unidade](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

   Quando você seleciona **Analisar Cobertura de Código**, as informações de configuração são lidas no arquivo de configurações de execução.

   > [!TIP]
   > Os resultados da cobertura de código e a coloração de código anteriores não são ocultados automaticamente quando você executa testes ou atualiza o código.

::: moniker range="vs-2017"

Para ativar ou desativar as configurações personalizadas, marque ou desmarque o arquivo no menu **Teste** > **Configurações do Teste**.

![Menu de configurações do teste com o arquivo de configurações personalizadas no Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Para ativar e ativar as configurações personalizadas, desmarque ou selecione o arquivo no menu **Teste.**

::: moniker-end

## <a name="symbol-search-paths"></a>Caminhos de busca de símbolos

A cobertura de código exige arquivos de símbolo (arquivos *.pdb*) para assemblies. Para assemblies compilados por sua solução, os arquivos de símbolos estão geralmente presentes nos arquivos binários e a cobertura de código funciona automaticamente. Em alguns casos, o ideal é incluir os assemblies referenciados na análise de cobertura de código. Nesses casos, os arquivos *.pdb* podem não estar adjacentes aos binários, mas você pode especificar o caminho de pesquisa de símbolos no arquivo *.runsettings.*

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> A resolução de símbolos pode ser demorada, especialmente ao usar um local de arquivo remoto com muitos assemblies. Portanto, considere copiar os arquivos *.pdb* no mesmo local que os arquivos binários (*.dll* e *.exe*).

## <a name="include-or-exclude-assemblies-and-members"></a>Incluir ou excluir assembléias e membros

Você pode incluir ou excluir assembléias ou tipos específicos e membros da análise de cobertura de código. Se a seção **Incluir** estiver vazia ou omitida, todos os conjuntos carregados e com arquivos PDB associados serão incluídos. Se uma assembléia ou membro corresponder a uma cláusula na seção **Excluir,** ela será excluída da cobertura de código. A seção **Excluir** tem precedência sobre a seção **Incluir:** se um conjunto estiver listado em **Incluir** e **Excluir,** ela não será incluída na cobertura de código.

Por exemplo, o XML a seguir exclui um único conjunto especificando seu nome:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

O exemplo a seguir especifica que apenas um único conjunto deve ser incluído na cobertura de código:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

A tabela a seguir mostra as várias maneiras pelas quais assembléias e membros podem ser combinados para inclusão ou exclusão da cobertura de código.

| Elemento XML | O que combina |
| - | - |
| ModulePath | Corresponde aos conjuntos especificados pelo nome do conjunto ou pelo caminho do arquivo. |
| CompanyName | Corresponde às assembléias pelo atributo **da Companhia.** |
| PublicKeyToken | Partidas assinadas assembléias pelo token de chave pública. |
| Fonte | Corresponde aos elementos pelo nome do caminho do arquivo de origem no qual eles são definidos. |
| Atributo | Corresponde aos elementos que têm o atributo especificado. Especifique o nome completo do atributo, por exemplo, `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`.<br/><br/>Se você excluir o atributo <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute>, o código que usa recursos de linguagem, como `async`, `await`, `yield return` e as propriedades implementadas automaticamente serão excluídas da análise de cobertura de código. Para excluir o código verdadeiramente gerado, exclua apenas o atributo <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. |
| Função | Corresponde a procedimentos, funções ou métodos por nome totalmente qualificado, incluindo a lista de parâmetros. Você também pode combinar parte do nome usando uma [expressão regular](#regular-expressions).<br/><br/>Exemplos:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)`(C++) |

### <a name="regular-expressions"></a>Expressões regulares

Os nós de inclusão e exclusão usam expressões regulares, que não são iguais aos curingas. Todas as correspondências não diferenciam maiúsculas de minúsculas. Alguns exemplos são:

- **. \* ** corresponde a uma seqüência de qualquer caractere

- **\\.** corresponde a um ponto "."

- ( ) corresponde aos parênteses "( )" ** \\ \\**

- **\\\\**corresponde a um delimitador de caminho de arquivo "\\"

- **^** corresponde ao início da seqüência

- **$** corresponde ao final da seqüência

O XML a seguir mostra como incluir e excluir conjuntos específicos usando expressões regulares:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

O XML a seguir mostra como incluir e excluir funções específicas usando expressões regulares:

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

> [!WARNING]
> Se houver um erro em uma expressão regular, como um parêntese sem correspondência ou sem escape, a análise de cobertura de código não será executada.

Para obter mais informações sobre expressões regulares, consulte [Usar expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>Arquivo .runsettings de exemplo

Copie esse código e edite-o para atender às suas necessidades.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Confira também

- [Configurar testes de unidade usando um arquivo de configurações de execução](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Usar a cobertura de código para determinar quanto do código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Unidade teste seu código](../test/unit-test-your-code.md)
