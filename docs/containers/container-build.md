---
title: Visual Studio Container Tools construir e depurar visão geral
author: ghogen
description: Visão geral do processo de compilação e depuração de ferramentas de contêiner
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: d91dd01879ac3bb62b981109463f6762046382ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027270"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Como o Visual Studio cria aplicativos em contêineres

Se você está construindo a partir do Visual Studio IDE, ou configurando uma compilação de linha de comando, você precisa saber como o Visual Studio usa o Arquivo Docker para construir seus projetos.  Por razões de desempenho, o Visual Studio segue um processo especial para aplicativos contêiner. Entender como o Visual Studio constrói seus projetos é especialmente importante quando você personaliza seu processo de compilação modificando o arquivo Docker.

Quando o Visual Studio constrói um projeto que não usa contêineres Docker, ele invoca o MSBuild na `bin`máquina local e gera os arquivos de saída em uma pasta (normalmente) sua pasta de solução local. Para um projeto contêiner, no entanto, o processo de compilação leva em conta as instruções do Arquivo Docker para a construção do aplicativo contêiner. O arquivo Docker que o Visual Studio usa é dividido em vários estágios. Esse processo conta com o recurso de *compilação multiestágio* do Docker.

## <a name="multistage-build"></a>Construção multiestágio

O recurso de compilação multiestágio ajuda a tornar o processo de construção de contêineres mais eficiente, e torna os contêineres menores, permitindo que eles contenham apenas os bits que seu aplicativo precisa em tempo de execução. A compilação multiestágio é usada para projetos .NET Core, não para projetos .NET Framework.

A compilação multiestágio permite que imagens de contêineres sejam criadas em estágios que produzem imagens intermediárias. Como exemplo, considere um arquivo Docker típico gerado pelo `base`Visual Studio - o primeiro estágio é :

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

As linhas no arquivo Docker começam com a imagem Debian do Microsoft `base` Container Registry (mcr.microsoft.com) e criam uma imagem intermediária `/app`que expõe as portas 80 e 443 e define maçanetas para .

A próxima `build`etapa é, que aparece da seguinte forma:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Você pode ver `build` que o estágio começa a`sdk` partir `aspnet`de uma imagem original diferente do registro (em vez de), em vez de continuar a partir da base.  A `sdk` imagem tem todas as ferramentas de compilação, e por isso é muito maior do que a imagem aspnet, que contém apenas componentes de tempo de execução. A razão para usar uma imagem separada torna-se clara quando você olha para o resto do Arquivo Docker:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

A etapa final `base`começa novamente a `COPY --from=publish` partir de , e inclui a cópia da saída publicada para a imagem final. Esse processo permite que a imagem final seja bem menor, já que não precisa incluir todas `sdk` as ferramentas de compilação que estavam na imagem.

## <a name="building-from-the-command-line"></a>Construindo a partir da linha de comando

Se você quiser construir fora do Visual `docker build` `MSBuild` Studio, você pode usar ou construir a partir da linha de comando.

### <a name="docker-build"></a>docker build

Para construir uma solução contêiner a partir da linha `docker build <context>` de comando, você geralmente pode usar o comando para cada projeto na solução. Você fornece o argumento de *contexto de construção.* O *contexto de construção* de um arquivo Docker é a pasta na máquina local que é usada como pasta de trabalho para gerar a imagem. Por exemplo, é a pasta que você copia arquivos de quando você copia para o contêiner.  Em projetos .NET Core, use a pasta que contém o arquivo de solução (.sln).  Expresso como um caminho relativo, esse argumento é tipicamente ".." para um arquivo Docker em uma pasta de projeto e o arquivo de solução em sua pasta pai.  Para projetos .NET Framework, o contexto de construção é a pasta do projeto, não a pasta de solução.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Os arquivos dockercriados pelo Visual Studio para projetos .NET Framework (e para projetos .NET Core criados com versões do Visual Studio antes do Visual Studio 2017 Update 4) não são arquivos Docker multiestágio.  As etapas nestes Arquivos Docker não compilam seu código.  Em vez disso, quando o Visual Studio constrói um Arquivo De seleção Framework .NET, ele primeiro compila seu projeto usando o MSBuild.  Quando isso for bem sucedido, o Visual Studio cria o Arquivo Docker, que simplesmente copia a saída de compilação do MSBuild para a imagem do Docker resultante.  Como as etapas para compilar seu código não estão incluídas no Arquivo Docker, você não pode criar arquivos .NET Framework Dockerusando `docker build` a partir da linha de comando. Você deve usar o MSBuild para construir esses projetos.

Para construir uma imagem para um único projeto de `/t:ContainerBuild` contêiner docker, você pode usar o MSBuild com a opção de comando. Por exemplo: 

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Você verá saída semelhante ao que você vê na janela **Saída** quando você constrói sua solução a partir do Visual Studio IDE. Sempre `/p:Configuration=Release`use , já que nos casos em que o Visual Studio usa a otimização de compilação multiestágio, os resultados ao construir a configuração **Debug** podem não ser como esperado. Consulte [Depuração](#debugging).

Se você estiver usando um projeto Dodocker Compose, use este comando para construir imagens:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Aquecimento do projeto

*O aquecimento* do projeto refere-se a uma série de etapas que acontecem quando o perfil do Docker é selecionado para um projeto (ou seja, quando um projeto é carregado ou o suporte ao Docker é adicionado) a fim de melhorar o desempenho das corridas subsequentes **(F5** ou **Ctrl**+**F5**). Isso é configurável em **Ferramentas** > **De Ferramentas De** > **Contêineres**. Aqui estão as tarefas que são executadas em segundo plano:

- Verifique se o Docker Desktop está instalado e em execução.
- Certifique-se de que o Docker Desktop está configurado para o mesmo sistema operacional que o projeto.
- Puxe as imagens no primeiro estágio `base` do Arquivo Docker (o estágio na maioria dos arquivos Docker).  
- Construa o arquivo Docker e inicie o recipiente.

O aquecimento só acontecerá no modo **Fast,** de modo que o contêiner em execução terá a pasta do aplicativo montada em volume. Isso significa que qualquer alteração no aplicativo não invalidará o contêiner. Isso melhora significativamente o desempenho da depuração e diminui o tempo de espera para tarefas de longa duração, como puxar imagens grandes.

## <a name="volume-mapping"></a>Mapeamento de volume

Para que a depuração funcione em contêineres, o Visual Studio usa mapeamento de volume para mapear as pastas dedepurador e NuGet da máquina host. O mapeamento de volume susta na documentação do Docker [aqui](https://docs.docker.com/storage/volumes/). Aqui estão os volumes que estão montados no seu recipiente:

|||
|-|-|
| **Depurador remoto** | Contém os bits necessários para executar o depurador no recipiente, dependendo do tipo de projeto. Isso é explicado em mais |detalhe na seção [Depuração.](#debugging)
| **Pasta de aplicativos** | Contém a pasta de projeto onde o Arquivo Docker está localizado.|
| **Pasta de origem** | Contém o contexto de construção que é passado para comandos Docker.|
| **Pastas de pacotes NuGet** | Contém os pacotes NuGet e pastas de recuo que são lidos do arquivo *\{obj project}.csproj.nuget.g.props* no projeto. |

Para ASP.NET principais aplicativos web, pode haver duas pastas adicionais para o certificado SSL e os segredos do usuário, o que é explicado com mais detalhes na próxima seção.

## <a name="ssl-enabled-aspnet-core-apps"></a>Aplicativos ASP.NET Core habilitados para SSL

As ferramentas de contêiner no Visual Studio suportam a depuração de um aplicativo principal de ASP.NET habilitado para SSL com um certificado de desenvolvimento, da mesma forma que você esperaria que funcionasse sem contêineres. Para que isso aconteça, o Visual Studio adiciona mais alguns passos para exportar o certificado e disponibilizá-lo para o contêiner. Aqui está o fluxo que o Visual Studio lida para você ao depurar no contêiner:

1. Garante que o certificado de desenvolvimento local esteja `dev-certs` presente e seja confiável na máquina host através da ferramenta.
2. Exporta o certificado para %APPDATA%\ASP.NET\Https com uma senha segura armazenada na loja de segredos do usuário para este aplicativo em particular.
3. O volume monta os seguintes diretórios:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\HTTPS*

ASP.NET Core procura um certificado que corresponda ao nome de montagem na pasta *Https,* razão pela qual ele é mapeado para o contêiner nesse caminho. O caminho do certificado e a senha podem ser `ASPNETCORE_Kestrel__Certificates__Default__Path` definidos alternativamente usando variáveis de ambiente (isto é, e `ASPNETCORE_Kestrel__Certificates__Default__Password`) ou no arquivo json segredos do usuário, por exemplo:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Se a configuração suportar construções contêinerizadas e não contêiner, você deve usar as variáveis do ambiente, porque os caminhos são específicos para o ambiente do contêiner.

Para obter mais informações sobre como usar o SSL com aplicativos ASP.NET Core em contêineres, consulte [Hosting ASP.NET Imagens Core com Docker sobre HTTPS](/aspnet/core/security/docker-https)).

## <a name="debugging"></a>Depuração

Ao construir na configuração **Debug,** existem várias otimizações que o Visual Studio faz que ajudam no desempenho do processo de construção para projetos em contêineres. O processo de compilação para aplicativos contêiner não é tão simples quanto simplesmente seguir as etapas descritas no Arquivo Docker. Construir em um contêiner é muito mais lento do que construir na máquina local.  Assim, quando você constrói na configuração **Debug,** o Visual Studio realmente constrói seus projetos na máquina local e, em seguida, compartilha a pasta de saída para o contêiner usando a montagem de volume. Uma compilação com essa otimização ativada é chamada de compilação de modo *rápido.*

No modo **Fast,** `docker build` o Visual Studio chama com `base` um argumento que diz ao Docker para construir apenas o palco.  O Visual Studio lida com o resto do processo sem levar em conta o conteúdo do Arquivo Docker. Assim, quando você modificar seu Arquivo Docker, como personalizar o ambiente do contêiner ou instalar dependências adicionais, você deve colocar suas modificações no primeiro estágio.  Quaisquer etapas personalizadas colocadas `build` `publish`no `final` Arquivo Docker, ou estágios não serão executadas.

Essa otimização de desempenho só ocorre quando você constrói na configuração **Debug.** Na configuração **'Liberar',** a compilação ocorre no contêiner conforme especificado no Arquivo Docker.

Se você quiser desativar a otimização de desempenho e a compilação conforme o Arquivo Docker especifica, defina a propriedade **ContainerDevelopmentMode** como **Regular** no arquivo do projeto da seguinte forma:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Para restaurar a otimização de desempenho, remova a propriedade do arquivo do projeto.

 Quando você começa a depurar **(F5),** um recipiente iniciado anteriormente é reutilizado, se possível. Se você não quiser reutilizar o recipiente anterior, você pode usar os comandos **Rebuild** ou **Clean** no Visual Studio para forçar o Visual Studio a usar um recipiente fresco.

O processo de execução do depurador depende do tipo de projeto e sistema operacional de contêineres:

|||
|-|-|
| **.NET Core apps (contêineres Linux)**| O Visual `vsdbg` Studio baixa e mapeia-o para o contêiner, em `dotnet webapp.dll`seguida, ele é chamado com o seu programa e argumentos (isto é, ), e, em seguida, depurador anexa-se ao processo. |
| **.NET Core apps (contêineres do Windows)**| Visual Studio `onecoremsvsmon` usa e mapeia-o para o contêiner, executa-o como o ponto de entrada e, em seguida, o Visual Studio se conecta a ele e anexa-se ao seu programa. Isso é semelhante ao que você normalmente configuraria depuração remota em outro computador ou máquina virtual.|
| **.NET Framework apps** | Visual Studio `msvsmon` usa e mapeia-o para o contêiner, executa-o como parte do ponto de entrada onde o Visual Studio pode se conectar a ele e anexa-se ao seu programa.|

Para obter `vsdbg.exe`informações sobre , consulte [Offroad depuração de .NET Core no Linux e OSX do Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Ponto de entrada do contêiner

O Visual Studio usa um ponto de entrada de contêiner personalizado, dependendo do tipo de projeto e do sistema operacional do contêiner, aqui estão as diferentes combinações:

|||
|-|-|
| **Contêineres Linux** | O ponto `tail -f /dev/null`de entrada é , que é uma espera infinita para manter o contêiner funcionando. Quando o aplicativo é lançado através do depurador, é o depurador que `dotnet webapp.dll`é responsável por executar o aplicativo (isto é, ). Se for iniciado sem depuração, a ferramenta executa um `docker exec -i {containerId} dotnet webapp.dll` para executar o aplicativo.|
| **Contêineres windows**| O ponto de `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` entrada é algo como o que executa o depurador, por isso está ouvindo conexões. O mesmo se aplica que o depurador executa o aplicativo e um `docker exec` comando quando iniciado sem depuração. Para aplicativos web .NET Framework, o `ServiceMonitor` ponto de entrada é ligeiramente diferente onde é adicionado ao comando.|

O ponto de entrada do contêiner só pode ser modificado em projetos de composição de docker, não em projetos de contêiner único.

## <a name="next-steps"></a>Próximas etapas

Aprenda a personalizar suas compilações definindo propriedades adicionais do MSBuild em seus arquivos de projeto. Consulte [as propriedades MSBuild para projetos de contêineres](container-msbuild-properties.md).

## <a name="see-also"></a>Confira também

[MSBuild](../msbuild/msbuild.md)
[Dockerfile em](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
contêineres Windows[Linux no Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
