---
title: Visão geral da compilação das ferramentas de contêiner do Visual Studio
author: ghogen
description: Visão geral do processo de Build das ferramentas de contêiner
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 9f2da112bfeebe4e0bce976736eee5696d888105
ms.sourcegitcommit: c7b9ab1bc19d74b635c19b1937e92c590dafd736
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2019
ms.locfileid: "70312191"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Criando aplicativos em contêineres usando o Visual Studio ou a linha de comando

Independentemente de você estar criando a partir do IDE do Visual Studio ou configurando uma compilação de linha de comando, você precisa saber como o Visual Studio compila usa o Dockerfile para criar seus projetos.  Por motivos de desempenho, o Visual Studio segue um processo especial para aplicativos em contêineres. Entender como o Visual Studio cria seus projetos é especialmente importante quando você personaliza o processo de compilação modificando o Dockerfile.

Quando o Visual Studio cria um projeto que não usa contêineres do Docker, ele invoca o MSBuild no computador local e gera os arquivos de saída em uma `bin`pasta (normalmente) em sua pasta de solução local. No entanto, para um projeto em contêineres, o processo de compilação conta com as instruções do Dockerfile para criar o aplicativo em contêineres. O Dockerfile que o Visual Studio usa é dividido em vários estágios. Esse processo depende do recurso de Build de vários *estágios* do Docker.

## <a name="multistage-build"></a>Build de multiestágio

O recurso de compilação de vários estágios ajuda a tornar o processo de criação de contêineres mais eficiente e torna os contêineres menores, permitindo que eles contenham apenas os bits de que seu aplicativo precisa no tempo de execução. A compilação de vários estágios é usada para projetos do .NET Core, não .NET Framework projetos.

O Build de multiestágio permite que as imagens de contêiner sejam criadas em estágios que produzem imagens intermediárias. Como exemplo, considere um típico Dockerfile gerado pelo Visual Studio – o primeiro estágio é `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

As linhas no Dockerfile começam com a imagem de beserver do MCR.Microsoft.com (registro de contêiner da Microsoft) e criam uma `base` imagem intermediária que expõe as portas 80 e 443 e define o diretório `/app`de trabalho como.

O próximo estágio é `build`, que aparece da seguinte maneira:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Você pode ver que o `build` estágio inicia de uma imagem original diferente do registro (`sdk` em vez de `aspnet`), em vez de continuar da base.  A `sdk` imagem tem todas as ferramentas de compilação e, por esse motivo, é muito maior do que a imagem ASPNET, que contém apenas componentes de tempo de execução. O motivo para usar uma imagem separada fica claro quando você examina o restante do Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

O estágio final inicia novamente de `base`e inclui o `COPY --from=publish` para copiar a saída publicada para a imagem final. Esse processo possibilita que a imagem final seja muito menor, pois não precisa incluir todas as ferramentas de compilação que estavam na `sdk` imagem.

## <a name="faster-builds-for-the-debug-configuration"></a>Builds mais rápidos para a configuração de depuração

Há várias otimizações que o Visual Studio faz para ajudar com o desempenho do processo de compilação para projetos em contêineres. Quando você inicia a depuração (F5), uma imagem criada anteriormente é reutilizada, se possível. Se você não quiser reutilizar o contêiner anterior, poderá usar os comandos **recriar** ou **limpar** no Visual Studio para forçar o Visual Studio a usar um contêiner novo.

Além disso, para melhorar o desempenho, o processo de compilação para aplicativos em contêineres não é tão simples quanto simplesmente seguir as etapas descritas no Dockerfile. A criação de um contêiner é muito mais lenta do que a criação no computador local.  Portanto, quando você cria a configuração de **depuração** , o Visual Studio realmente cria seus projetos no computador local e compartilha a pasta de saída para o contêiner usando a montagem de volume. Uma compilação com essa otimização habilitada é chamada de compilação de modo *rápido* .

No modo **rápido** , o Visual Studio `docker build` chama um argumento que informa ao Docker para compilar apenas `base` o estágio.  O Visual Studio lida com o restante do processo sem considerar o conteúdo do Dockerfile. Portanto, quando você modifica seu Dockerfile, como para personalizar o ambiente de contêiner ou instalar dependências adicionais, você deve colocar suas modificações no primeiro estágio.  Todas as etapas personalizadas colocadas nos estágios do `build`Dockerfile `publish`, ou `final` não serão executadas.

Essa otimização de desempenho ocorre apenas quando você cria na configuração de **depuração** . Na configuração da **versão** , a compilação ocorre no contêiner, conforme especificado no Dockerfile.

Se você quiser desabilitar a otimização de desempenho e compilar como o Dockerfile especifica, defina a propriedade **ContainerDevelopmentMode** como **regular** no arquivo de projeto da seguinte maneira:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Para restaurar a otimização de desempenho, remova a propriedade do arquivo de projeto.

## <a name="building-from-the-command-line"></a>Criando a partir da linha de comando

Você pode usar `docker build` ou `MSBuild` para criar a partir da linha de comando.

### <a name="docker-build"></a>Build do Docker

Para criar uma solução em contêiner a partir da linha de comando, você geralmente pode usar `docker build <context>` o comando para cada projeto na solução. Você fornece o argumento de *contexto de compilação* . O *contexto de compilação* para um Dockerfile é a pasta no computador local que é usada como a pasta de trabalho para gerar a imagem. Por exemplo, é a pasta da qual você copia arquivos quando você copia para o contêiner.  Em projetos do .NET Core, use a pasta que contém o arquivo de solução (. sln).  Expresso como um caminho relativo, esse argumento normalmente é ".." para um Dockerfile em uma pasta de projeto e o arquivo de solução em sua pasta pai.  Para projetos .NET Framework, o contexto de compilação é a pasta do projeto, não a pasta da solução.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Dockerfiles criados pelo Visual Studio para projetos de .NET Framework (e para projetos do .NET Core criados com versões do Visual Studio anteriores ao Visual Studio 2017 atualização 4) não são Dockerfiles de vários estágios.  As etapas nesses Dockerfiles não compilam seu código.  Em vez disso, quando o Visual Studio cria um .NET Framework Dockerfile, ele primeiro compila seu projeto usando o MSBuild.  Quando isso for executado com sucesso, o Visual Studio criará o Dockerfile, que simplesmente copia a saída da compilação do MSBuild para a imagem do Docker resultante.  Como as etapas para compilar seu código não estão incluídas no Dockerfile, você não pode criar .NET Framework Dockerfiles `docker build` usando a partir da linha de comando. Você deve usar o MSBuild para compilar esses projetos.

Para criar uma imagem para um único projeto de contêiner do Docker, você pode `/t:ContainerBuild` usar o MSBuild com a opção de comando. Por exemplo:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Você verá uma saída semelhante à que você vê na janela de **saída** ao compilar sua solução no IDE do Visual Studio. Sempre use `/p:Configuration=Release`, como nos casos em que o Visual Studio usa a otimização de compilação de multiestágio, os resultados na criação da configuração de **depuração** podem não ser conforme o esperado.

Se você estiver usando um projeto Docker Compose, use o comando para criar imagens:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Próximas etapas

Saiba como personalizar ainda mais suas compilações definindo propriedades adicionais do MSBuild em seus arquivos de projeto. Consulte [Propriedades do MSBuild para projetos de contêiner](container-msbuild-properties.md).

## <a name="see-also"></a>Consulte também

[MSBuild](../msbuild/msbuild.md)
[ Dockerfile em contêineres Linux do Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[ no Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
