---
title: Ferramentas de contêineres do Visual Studio constroem propriedades
author: ghogen
description: Visão geral do processo de compilação de ferramentas de contêiner
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71950694"
---
# <a name="container-tools-build-properties"></a>Ferramentas de contêiner constroem propriedades

Você pode personalizar como o Visual Studio constrói seus projetos de contêineres definindo as propriedades que o MSBuild usa para construir seu projeto. Por exemplo, você pode alterar o nome do Arquivo Docker, especificar tags e rótulos para suas imagens, fornecer argumentos adicionais passados para comandos Docker e controlar se o Visual Studio faz certas otimizações de desempenho, como construir fora do ambiente de contêiner. Você também pode definir propriedades de depuração, como o nome do executável para inicial, e os argumentos da linha de comando a serem fornecidos.

Para definir o valor de uma propriedade, edite o arquivo do projeto. Por exemplo, suponha que seu Arquivo Docker se chama *MyDockerfile*. Você pode `DockerfileFile` definir a propriedade no arquivo do projeto da seguinte forma.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Você pode adicionar a configuração `PropertyGroup` de propriedade a um elemento existente, `PropertyGroup` ou se não houver um, criar um novo elemento.

A tabela a seguir mostra as propriedades mSBuild disponíveis para projetos de contêineres. A versão do pacote NuGet se aplica ao [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nome da propriedade | Descrição | Valor padrão  | Versão do pacote NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Controla se a otimização "build-on-host" (depuração do "Modo Rápido" está ativada.  Os valores permitidos são **Rápidos** e **Regulares**. | Rápido |1.0.1872750 ou mais novo|
| ContainerVsDbgPath | O caminho para o depurador VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 ou mais novo|
| DockerDebuggeeArguments | Ao depurar, o depurador é instruído a passar esses argumentos para o executável iniciado. | Não aplicável a ASP.NET projetos do Framework .NET |1.7.8 ou mais novo|
| DockerDebuggeeProgram | Ao depurar, o depurador é instruído a iniciar este executável. | Para projetos .NET Core: dotnet, ASP.NET .NET Framework projects: Não aplicável (IIS é sempre usado) |1.7.8 ou mais novo|
| DockerDebuggeeKillProgram | Este comando é usado para matar o processo de execução em um contêiner. | Não aplicável a ASP.NET projetos do Framework .NET |1.7.8 ou mais novo|
| DockerDebuggeeWorkingDirectory | Ao depurar, o depurador é instruído a usar esse caminho como o diretório de trabalho. | C:\app (Windows) ou /app (Linux) |1.7.8 ou mais novo|
| DockerDefaultTargetOS | O sistema operacional de destino padrão usado ao construir a imagem Docker. | Definido por Visual Studio. |1.0.1985401 ou mais novo|
| DockerImageRótulos | O conjunto padrão de rótulos aplicados à imagem do Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 ou mais novo|
| DockerFastModeProjectMountDirectory|No **Modo Rápido,** esta propriedade controla onde o diretório de saída do projeto é montado em volume no contêiner em execução.|C:\app (Windows) ou /app (Linux)|1.9.2 ou mais novo|
| DockerfileBuildArguments | Argumentos adicionais passaram para o comando de compilação do Docker. | Não aplicável. |1.0.1872750 ou mais novo|
| DockerfileContext | O contexto padrão usado ao construir a imagem Docker. | Definido por Visual Studio. |1.0.1872750 ou mais novo|
| DockerfileFastModeStage | O estágio Dockerfile (ou seja, alvo) a ser usado ao construir a imagem no modo de depuração. | Primeiro estágio encontrado no Arquivo Docker (base) |
| Arquivo de arquivo docker | Descreve o arquivo Docker padrão que será usado para construir/executar o contêiner para o projeto. Este pode ser um caminho também. | Dockerfile |1.0.1872750 ou mais novo|
| DockerfileRunArguments | Argumentos adicionais passaram para o comando de execução do Docker. | Não aplicável. |1.0.1872750 ou mais novo|
| Arquivo de dockersExecutararquivosdeambiente | Lista delimitada de ponto e vírgula de arquivos de ambiente aplicados durante a execução do Docker. | Não aplicável. |1.0.1872750 ou mais novo|
| DockerfileTag | A tag que será usada ao construir a imagem do Docker. Na depuração, um ":dev" é anexado à tag. | Nome de montagem após a retirada de caracteres não alfanuméricos com as seguintes regras: <br/> Se a tag resultante for toda numérica, então "imagem" será inserida como um prefixo (por exemplo, imagem2314) <br/> Se a tag resultante for uma seqüência de string vazia, então "image" será usado como tag. |1.0.1872750 ou mais novo|

## <a name="next-steps"></a>Próximas etapas

Para obter informações sobre propriedades MSBuild em geral, consulte [MSBuild Properties](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Confira também

[Docker Compor propriedades de construção](docker-compose-properties.md)

[Configurações de lançamento do Container Tools](container-launch-settings.md)

[MSBuild propriedades reservadas e bem conhecidas](../msbuild/msbuild-reserved-and-well-known-properties.md)
