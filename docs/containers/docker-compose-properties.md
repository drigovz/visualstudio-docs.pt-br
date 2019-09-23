---
title: Ferramentas de contêiner do Visual Studio Docker Compose configurações de compilação
author: ghogen
description: Visão geral do processo de Build das ferramentas de contêiner
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 06a1c5b637ca2ed9306162ee1960c60d103e5843
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185974"
---
# <a name="docker-compose-build-properties"></a>Docker Compose Propriedades de compilação

Além das propriedades que controlam projetos individuais do Docker, descritas em [ferramentas de contêiner Propriedades de compilação](container-msbuild-properties.md), você também pode personalizar como o Visual Studio cria seus projetos de Docker Compose definindo as propriedades de Docker Compose que o MSBuild usa para compilar sua solução. Você também pode controlar como o depurador do Visual Studio executa seus aplicativos Docker Compose definindo rótulos de arquivo em Docker Compose arquivos de configuração.

## <a name="how-to-set-the-msbuild-properties"></a>Como definir as propriedades do MSBuild

Para definir o valor de uma propriedade, edite o arquivo de projeto. Para propriedades Docker Compose, esse arquivo de projeto é aquele com uma extensão. dcproj, a menos que indicado em contrário na tabela na próxima seção. Por exemplo, suponha que você queira especificar para iniciar o navegador quando iniciar a depuração. Você pode definir a `DockerLaunchAction` Propriedade no arquivo de projeto. dcproj da seguinte maneira.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Você pode adicionar a configuração de propriedade a um `PropertyGroup` elemento existente ou, se não houver um, crie um `PropertyGroup` novo elemento.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose Propriedades do MSBuild

A tabela a seguir mostra as propriedades do MSBuild disponíveis para projetos Docker Compose.

| Property name | Local | Descrição | Valor padrão  |
|---------------|----------|-------------|----------------|
|DockerComposeBuildArguments|dcproj|Especifica os parâmetros extras a serem passados para `docker-compose build` o comando. Por exemplo, `--parallel --pull` |
|DockerComposeDownArguments|dcproj|Especifica os parâmetros extras a serem passados para `docker-compose down` o comando. Por exemplo, `--timeout 500`|-|  
|DockerComposeProjectPath|csproj ou vbproj|O caminho relativo para o arquivo de projeto do Docker-Compose (dcproj). Defina essa propriedade ao publicar o projeto de serviço para localizar as configurações de Build de imagem associadas armazenadas no arquivo Docker-Compose. yml.|-|
|DockerComposeUpArguments|dcproj|Especifica os parâmetros extras a serem passados para `docker-compose up` o comando. Por exemplo, `--timeout 500`|-|
|DockerLaunchAction| dcproj | Especifica a ação de inicialização a ser executada em F5 ou CTRL + F5.  Os valores permitidos são None, LaunchBrowser e LaunchWCFTestClient|Nenhum|
|DockerLaunchBrowser| dcproj | Indica se o navegador deve ser iniciado. Ignorado se DockerLaunchAction for especificado. | False |
|DockerServiceName| dcproj|Se DockerLaunchAction ou DockerLaunchBrowser forem especificados, DockerServiceName será o nome do serviço que deve ser iniciado.  Use essa propriedade para determinar qual dos possíveis projetos que podem ser referenciados por um arquivo Docker-Compose será iniciado.|-|
|DockerServiceUrl| dcproj | A URL a ser usada ao iniciar o navegador.  Os tokens de substituição válidos são "{% IPAddress}", "{ServicePortal}" e "{Scheme}".  Por exemplo: {Scheme}://{ServiceIPAddress}: {ServicePortal}|-|
|DockerTargetOS| dcproj | O sistema operacional de destino usado ao criar a imagem do Docker.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments e DockerComposeUpArguments são novos no Visual Studio 2019 versão 16,3 Preview 3.

## <a name="docker-compose-file-labels"></a>Docker Compose rótulos de arquivo

Você também pode substituir determinadas configurações colocando um arquivo chamado *Docker-Compose. vs. Debug. yml* (para a configuração de **depuração** ) ou *Docker-Compose. vs. Release. yml* (para a configuração de **versão** ) no mesmo diretório que o seu  *arquivo Docker-Compose. yml* .  Nesse arquivo, você pode especificar as configurações da seguinte maneira:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Use aspas duplas em volta dos valores, como no exemplo anterior, e use a barra invertida como um caractere de escape para barras invertidas em caminhos.

|Nome do rótulo|Descrição|
|----------|-----------|
|com. Microsoft. VisualStudio. Depurando. Arguments|Os argumentos passados para o programa ao iniciar a depuração. Para aplicativos .NET Core, esses argumentos normalmente são caminhos de pesquisa adicionais para pacotes NuGet seguidos pelo caminho para o assembly de saída do projeto.|
|com. Microsoft. VisualStudio. Depurando. killprogram|Esse comando é usado para parar o programa que está sendo depurado em execução dentro do contêiner (quando necessário).|
|com. Microsoft. VisualStudio. Depurando. programa|O programa foi iniciado ao iniciar a depuração. Para aplicativos .NET Core, essa configuração normalmente é **dotnet**.|
|com. Microsoft. VisualStudio. Depurando. WorkingDirectory|O diretório usado como o diretório inicial ao iniciar a depuração. Essa configuração normalmente é */app* para contêineres do Linux ou *C:\app* para contêineres do Windows.|

## <a name="next-steps"></a>Próximas etapas

Para obter informações sobre propriedades do MSBuild em geral, consulte [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Consulte também

[Propriedades de compilação das ferramentas de contêiner](container-msbuild-properties.md)

[Configurações de inicialização das ferramentas de contêiner](container-launch-settings.md)

[Propriedades reservadas e conhecidas do MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
