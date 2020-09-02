---
title: Compilar e compilar código TypeScript usando o NuGet
description: Saiba como compilar e compilar TypeScript no Visual Studio.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ac917248915129b8d93dc776ac7d35a2ed227069
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87454587"
---
# <a name="compile-typescript-code-aspnet-core"></a>Compilar código TypeScript (ASP.NET Core)

Você pode adicionar suporte do TypeScript aos seus projetos usando o TypeScript SDK, disponível por padrão no instalador do Visual Studio ou usando o pacote NuGet. Para projetos desenvolvidos no Visual Studio 2019, incentivamos você a usar o NuGet do TypeScript para maior portabilidade em diferentes plataformas e ambientes.

Para projetos ASP.NET Core, um uso comum para o pacote NuGet é compilar TypeScript usando o CLI do .NET Core. A menos que você edite manualmente o arquivo de projeto para importar destinos de compilação de uma instalação do TypeScript SDK, o pacote NuGet é a única maneira de habilitar a compilação do TypeScript usando comandos CLI do .NET Core como `dotnet build` e `dotnet publish` . Além disso, para a [integração do MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) com o ASP.NET Core e o TypeScript, escolha o pacote NuGet no pacote NPM.

## <a name="add-typescript-support-with-nuget"></a>Adicionar suporte ao TypeScript com o NuGet

[O pacote NuGet do typescript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) adiciona suporte a typescript. Quando o pacote do NuGet para o TypeScript 3.2 ou posterior está instalado em seu projeto, a versão correspondente do serviço de linguagem TypeScript é carregada no editor.

Se o Visual Studio estiver instalado, o node.exe agrupado com ele será automaticamente coletado pelo Visual Studio. Se você não tiver Node.js instalado, recomendamos que instale a versão LTS do site do [Node.js](https://nodejs.org/en/download/) .

1. Abra seu projeto de ASP.NET Core no Visual Studio.

1. Na Gerenciador de Soluções (painel direito). Clique com o botão direito do mouse no nó do projeto e escolha **gerenciar pacotes NuGet**. Na guia **procurar** , procure **Microsoft. TypeScript. MSBuild**e clique em **instalar** à direita para instalar o pacote.

   ![Adicionar pacote NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   O Visual Studio adiciona o pacote NuGet sob o nó **dependências** em Gerenciador de soluções. A referência de pacote a seguir é adicionada ao seu arquivo *. csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Clique com o botão direito do mouse no nó do projeto e escolha **adicionar > novo item**. Escolha o **arquivo de configuração JSON do TypeScript**e clique em **Adicionar**.

   O Visual Studio adiciona o *tsconfig.jsno* arquivo à raiz do projeto. Você pode usar esse arquivo para [Configurar opções](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) para o compilador TypeScript.

1. Abra o *tsconfig.jsem* e atualize para definir as opções de compilador que você deseja.

   Veja a seguir um exemplo de um *tsconfig.jssimples no* arquivo.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Neste exemplo:
   - *include* informa ao compilador onde encontrar arquivos TypeScript (*. TS).
   - a opção *outDir* especifica a pasta de saída para os arquivos JavaScript simples que são transcompilados pelo compilador do TypeScript.
   - a opção *sourceMap* indica se o compilador gera arquivos *sourceMap* .

   A configuração anterior fornece apenas uma introdução básica à configuração do TypeScript. Para obter informações sobre outras opções, consulte [tsconfig.jsem](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

### <a name="build-the-application"></a>Compilar o aplicativo

1. Adicione arquivos TypeScript (*. TS*) ou typescript JSX (*. TSX*) ao seu projeto e, em seguida, adicione o código TypeScript. Para obter um exemplo simples de TypeScript, use o seguinte:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Se você estiver usando um projeto de estilo não-SDK mais antigo, siga as instruções em [remover importações padrão](#remove-default-imports) antes de Compilar.

1. Escolha **compilar > Compilar solução**.

   Embora o aplicativo seja criado automaticamente quando você o executa, queremos dar uma olhada em algo que acontece durante o processo de compilação:

   Se você gerou mapas de origem, abra a pasta especificada na opção *outDir* e localize os arquivos *. js gerados juntamente com os arquivos * js. map gerados.

   Os arquivos de mapa de origem são necessários para depuração.

1. Se você quiser compilar toda vez que salvar o projeto, use a opção *compileOnSave* em *. tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Para obter um exemplo de como usar Gulp com o executor de tarefa para criar seu aplicativo, consulte [ASP.NET Core e TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Se você encontrar problemas em que o Visual Studio está usando uma versão do Node.js ou uma ferramenta de terceiros que seja diferente da versão esperada, talvez seja necessário definir o caminho do Visual Studio a ser usado. Escolha **ferramentas**  >  **Opções**. Em **projetos e soluções**, escolha **Web gerenciamento de pacotes**  >  **ferramentas Web externas**.

### <a name="nuget-package-structure-details"></a>Detalhes da estrutura do pacote NuGet

`Microsoft.TypeScript.MSBuild.nupkg` contém duas pastas principais:

- pasta de *Build*

    Dois arquivos estão localizados nessa pasta.
    Ambos são pontos de entrada-para o arquivo de destino do TypeScript principal e o arquivo de propriedades, respectivamente.

    1. *Microsoft. TypeScript. MSBuild. targets*

        Esse arquivo define variáveis que especificam a plataforma de tempo de execução, como um caminho para *TypeScript.Tasks.dll*, antes de importar *Microsoft. TypeScript. targets* da pasta *Tools* .

    2. *Microsoft. TypeScript. MSBuild. props*

        Esse arquivo importa *Microsoft. TypeScript. default. props* da pasta *Tools* e define as propriedades indicando que a compilação foi iniciada por meio do NuGet.

- pasta de *ferramentas*

    As versões do pacote anteriores à 2,3 contêm apenas uma pasta TSC. *Microsoft. TypeScript. targets* e *TypeScript.Tasks.dll* estão localizados no nível raiz.

    Nas versões de pacote 2,3 e posteriores, o nível raiz contém `Microsoft.TypeScript.targets` e `Microsoft.TypeScript.Default.props` . Para obter mais detalhes sobre esses arquivos, consulte [configuração do MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Além disso, a pasta contém três subpastas:

    1. *net45*

        Essa pasta contém `TypeScript.Tasks.dll` e outras DLLs das quais ela depende.
        Ao criar um projeto em uma plataforma Windows, o MSBuild usa as DLLs dessa pasta.

    2. *netstandard1.3*

        Essa pasta contém outra versão do `TypeScript.Tasks.dll` , que é usada durante a compilação de projetos em um computador não Windows.

    3. *TSC*

        Essa pasta contém `tsc.js` `tsserver.js` e todos os arquivos de dependência necessários para executá-los como scripts de nó.

        > [!NOTE]
        > Se o Visual Studio estiver instalado, o *node.exe* agrupado com ele será automaticamente selecionado. Caso contrário Node.js deve ser instalado no computador.

        As versões anteriores a 3,1 continham um `tsc.exe` executável para executar a compilação. Na versão 3,1, isso foi removido em favor do uso do `node.exe` .

### <a name="remove-default-imports"></a>Remover importações padrão

Em projetos de ASP.NET Core mais antigos que usam o [formato de estilo não-SDK](https://docs.microsoft.com/nuget/resources/check-project-format), talvez seja necessário remover alguns elementos de arquivo de projeto.

Se você estiver usando o pacote NuGet para suporte do MSBuild para um projeto, o arquivo de projeto não deverá importar `Microsoft.TypeScript.Default.props` ou `Microsoft.TypeScript.targets` . Os arquivos são importados pelo pacote NuGet, portanto, incluí-los separadamente pode causar um comportamento indesejado.

1. Clique com o botão direito do mouse no projeto e escolha **descarregar projeto**.

1. Clique com o botão direito do mouse no projeto e escolha **Editar \<*project file name*\> **.

   O arquivo de projeto é aberto.

1. Remova as referências a `Microsoft.TypeScript.Default.props` e `Microsoft.TypeScript.targets` .

   As importações a serem removidas são semelhantes às seguintes:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
