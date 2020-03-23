---
title: Ferramentas de contêineres do Visual Studio Docker compõem configurações de compilação
author: ghogen
description: Visão geral do processo de compilação de ferramentas de contêiner
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 85cb8745a14439cfb09036a1bc96e6bd0fa15ae4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988512"
---
# <a name="docker-compose-build-properties"></a>Docker Compor propriedades de construção

Além das propriedades que controlam projetos individuais do Docker, descritos nas [propriedades de construção do Container Tools,](container-msbuild-properties.md)você também pode personalizar como o Visual Studio constrói seus projetos de Composição do Docker, definindo as propriedades do Docker Compose que o MSBuild usa para construir sua solução. Você também pode controlar como o depurador do Visual Studio executa seus aplicativos Do Docker Compose definindo rótulos de arquivos em arquivos de configuração do Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Como definir as propriedades do MSBuild

Para definir o valor de uma propriedade, edite o arquivo do projeto. Para propriedades Docker Compose, este arquivo de projeto é aquele com uma extensão .dcproj, a menos que indicado de outra forma na tabela na próxima seção. Por exemplo, suponha que você queira especificar para iniciar o navegador quando você começar a depurar. Você pode `DockerLaunchAction` definir a propriedade no arquivo do projeto .dcproj da seguinte forma.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Você pode adicionar a configuração `PropertyGroup` de propriedade a um elemento existente, `PropertyGroup` ou se não houver um, criar um novo elemento.

## <a name="docker-compose-msbuild-properties"></a>Propriedades do Docker Compose no MSBuild

A tabela a seguir mostra as propriedades mSBuild disponíveis para projetos do Docker Compose.

| Nome da propriedade | Location | Descrição | Valor padrão  |
|---------------|----------|-------------|----------------|
|Caminhos adicionais de filepaths|dcproj|Especifica arquivos adicionais de composição em uma lista delimitada de ponto e vírgula a ser enviada para docker-compose.exe para todos os comandos. Caminhos relativos do arquivo de projeto de composição de docker (dcproj) são permitidos.|-|
|DockerComposeBaseFilePath|dcproj|Especifica a primeira parte dos nomes de arquivos de composição de docker, sem a extensão *.yml.* Por exemplo:  <br>1. DockerComposeBaseFilePath = nulo/indefinido: use o caminho base do arquivo *docker-compor*, e os arquivos serão nomeados *docker-compose.yml* e *docker-compose.override.yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: os arquivos serão nomeados *mydockercompose.yml* e *mydockercompose.override.yml*<br> 3. DockerComposeBaseFilePath = *.. \mydockercom :* os arquivos subirão um nível. |docker-compor|
|DockerComComBuildArguments|dcproj|Especifica os parâmetros extras `docker-compose build` para passar para o comando. Por exemplo, `--parallel --pull` |
|DockerComDownArguments|dcproj|Especifica os parâmetros extras `docker-compose down` para passar para o comando. Por exemplo, `--timeout 500`|-|  
|DockerComComProjectPath|csproj ou vbproj|O caminho relativo para o arquivo de projeto de composição de docker (dcproj). Defina essa propriedade ao publicar o projeto de serviço para encontrar as configurações de compilação de imagem associadas armazenadas no arquivo docker-compose.yml.|-|
|DockerComposeUpArguments|dcproj|Especifica os parâmetros extras `docker-compose up` para passar para o comando. Por exemplo, `--timeout 500`|-|
|DockerDevelopmentMode|dcproj| Controla se a otimização "build-on-host" (depuração do "Modo Rápido" está ativada.  Os valores permitidos são **Rápidos** e **Regulares**. | Rápido |
|DockerLaunchAction| dcproj | Especifica a ação de lançamento a ser realizado em F5 ou Ctrl+F5.  Os valores permitidos são None, LaunchBrowser e LaunchWCFTestClient|Nenhum|
|DockerLaunchBrowser| dcproj | Indica se deve iniciar o navegador. Ignorado se o DockerLaunchAction for especificado. | Falso |
|DockerServiceName| dcproj|Se DockerLaunchAction ou DockerLaunchBrowser forem especificados, dockerServiceName é o nome do serviço que deve ser lançado.  Use esta propriedade para determinar qual dos vários projetos potencialmente muitos projetos que um arquivo de composição de docker pode referenciar será lançado.|-|
|DockerServiceUrl| dcproj | A URL para usar ao iniciar o navegador.  Os tokens de substituição válidos são "{ServiceIPAddress}", "{ServicePort}" e "{Scheme}".  Por exemplo: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | O sistema operacional de destino usado na construção da imagem do Docker.|-|

## <a name="example"></a>Exemplo

Se você alterar a localização dos arquivos `DockerComposeBaseFilePath` de composição do docker, definindo para um caminho relativo, então você também precisa ter certeza de que o contexto de compilação é alterado para que ele faça referência à pasta de solução. Por exemplo, se o arquivo de composição do docker for uma pasta chamada *DockerComposeFiles,* então o arquivo de composição de docker deve definir o contexto de compilação como ".." ou ".. /..", dependendo de onde está em relação à pasta de solução.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

O arquivo *mydockercompose.yml* deve ficar assim, com o contexto de construção definido para `..`o caminho relativo da pasta de solução (neste caso, ).

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments e DockerComposeUpArguments são novos na versão 16.3 do Visual Studio 2019.

## <a name="docker-compose-file-labels"></a>Rótulos de arquivo Docker Compose

Você também pode substituir certas configurações colocando um arquivo chamado *docker-compose.vs.debug.yml* (para configuração **Debug)** ou *docker-compose.vs.release.yml* (para configuração **de lançamento)** no mesmo diretório que o arquivo *docker-compose.yml.*  Neste arquivo, você pode especificar as configurações da seguinte forma:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Use aspas duplas em torno dos valores, como no exemplo anterior, e use a barra invertida como um caractere de fuga para cortes de corte em caminhos.

|Nome do rótulo|Descrição|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Os argumentos passaram para o programa ao iniciar a depuração. Para aplicativos .NET Core, esses argumentos são normalmente caminhos adicionais de pesquisa para pacotes NuGet seguidos do caminho para o conjunto de saída do projeto.|
|com.microsoft.visualstudio.debuggee.killprogram|Este comando é usado para parar o programa de depuração que está sendo executado dentro do contêiner (quando necessário).|
|com.microsoft.visualstudio.debuggee.program|O programa foi lançado ao iniciar a depuração. Para aplicativos .NET Core, essa configuração é tipicamente **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|O diretório usado como o diretório inicial ao iniciar a depuração. Esta configuração é tipicamente */app* para contêineres Linux ou *c:\app* para contêineres Windows.|

## <a name="customize-the-app-startup-process"></a>Personalize o processo de inicialização do aplicativo

Você pode executar um comando ou script personalizado `entrypoint` antes de iniciar seu aplicativo usando a configuração e tornando-o dependente da configuração. Por exemplo, se você precisar configurar um certificado apenas `update-ca-certificates`no modo **Debug** executando, mas não no modo **de lançamento,** você poderá adicionar o seguinte código apenas em *docker-compose.vs.debug.yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Se você omitir o *docker-compose.vs.release.yml* ou *docker-compose.vs.debug.yml,* então o Visual Studio gera um com base nas configurações padrão.

## <a name="next-steps"></a>Próximas etapas

Para obter informações sobre propriedades MSBuild em geral, consulte [MSBuild Properties](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Confira também

[Ferramentas de contêiner constroem propriedades](container-msbuild-properties.md)

[Configurações de lançamento do Container Tools](container-launch-settings.md)

[MSBuild propriedades reservadas e bem conhecidas](../msbuild/msbuild-reserved-and-well-known-properties.md)
