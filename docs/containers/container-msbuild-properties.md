---
title: Propriedades de compilação das ferramentas de contêiner do Visual Studio
author: ghogen
description: Visão geral do processo de Build das ferramentas de contêiner
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4bc6cb4221d85bd43b98b2ac36c34c919937960b
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70312030"
---
# <a name="container-tools-build-properties"></a>Propriedades de compilação das ferramentas de contêiner

Você pode personalizar como o Visual Studio cria seus projetos de contêiner definindo as propriedades que o MSBuild usa para criar seu projeto. Por exemplo, você pode alterar o nome do Dockerfile, especificar marcas e rótulos para suas imagens, fornecer argumentos adicionais passados para comandos do Docker e controlar se o Visual Studio realiza determinadas otimizações de desempenho, como a criação fora do ambiente de contêiner. Você também pode definir propriedades de depuração, como o nome do executável a ser iniciado, e os argumentos de linha de comando a serem fornecidos.

Para definir o valor de uma propriedade, edite o arquivo de projeto. Por exemplo, suponha que seu Dockerfile seja chamado de *MyDockerfile*. Você pode definir a `DockerfileFile` Propriedade no arquivo de projeto da seguinte maneira.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Você pode adicionar a configuração de propriedade a um `PropertyGroup` elemento existente ou, se não houver um, crie um `PropertyGroup` novo elemento.

A tabela a seguir mostra as propriedades do MSBuild disponíveis para projetos de contêiner.

| Nome da propriedade | Descrição | Valor padrão  |
|---------------|-------------|----------------|
| DockerfileFile | Descreve o Dockerfile padrão que será usado para compilar/executar o contêiner para o projeto. Isso também pode ser um caminho. | Dockerfile |
| DockerfileTag | A marca que será usada ao criar a imagem do Docker. Na depuração, um ":d EV" é acrescentado à marca. | Nome do assembly após a remoção de caracteres não alfanuméricos com as seguintes regras: <br/> Se a marca resultante for todos numéricas, "Image" será inserida como um prefixo (por exemplo, image2314) <br/> Se a marca resultante for uma cadeia de caracteres vazia, "Image" será usada como a marca. |
| DockerContext | O contexto padrão usado ao criar a imagem do Docker. | Definido pelo Visual Studio. |
| ContainerDevelopmentMode | Controla se a otimização "Build-on-host" (depuração "modo rápido") está habilitada.  Os valores permitidos são **rápido** e **regular**. | Rápido |
| DockerDefaultTargetOS | O sistema operacional de destino padrão usado ao criar a imagem do Docker. | Definido pelo Visual Studio. |
| DockerImageLabels | O conjunto padrão de rótulos aplicados à imagem do Docker. | com. Microsoft. Created-by = Visual-Studio; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |
| ContainerVsDbgPath | O caminho para o depurador VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |
| DockerfileBuildArguments | Argumentos adicionais passados para o comando de Build do Docker. | Não aplicável. |
| DockerfileRunArguments | Argumentos adicionais passados para o comando de execução do Docker. | Não aplicável. |
| DockerfileRunEnvironmentFiles | Lista delimitada por ponto e vírgula dos arquivos de ambiente aplicados durante a execução do Docker. | Não aplicável. |
| DockerfileFastModeStage | O estágio Dockerfile (ou seja, Target) a ser usado ao criar a imagem no modo de depuração. | Primeiro estágio encontrado no Dockerfile (base) |
| DockerDebuggeeProgram | Durante a depuração, o depurador é instruído a iniciar este executável. | Para projetos do .NET Core: dotnet, ASP.NET .NET Framework projetos: Não aplicável (o IIS é sempre usado) |
| DockerDebuggeeArguments | Durante a depuração, o depurador é instruído a passar esses argumentos para o executável iniciado. | Não aplicável a projetos de .NET Framework ASP.NET |
| DockerDebuggeeWorkingDirectory | Durante a depuração, o depurador é instruído a usar esse caminho como o diretório de trabalho. | C:\app (Windows) ou/app (Linux) |
| DockerDebuggeeKillProgram | Esse comando é usado para eliminar o processo em execução em um contêiner. | Não aplicável a projetos de .NET Framework ASP.NET |

## <a name="next-steps"></a>Próximas etapas

Para obter informações sobre propriedades do MSBuild em geral, consulte [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Consulte também

[Docker Compose Propriedades de compilação](docker-compose-properties.md)

[Configurações de inicialização das ferramentas de contêiner](container-launch-settings.md)

[Propriedades reservadas e conhecidas do MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
