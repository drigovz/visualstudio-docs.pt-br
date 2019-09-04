---
title: Ferramentas do Visual Studio para Contêineres com ASP.NET Core
author: ghogen
description: Saiba como usar as Ferramentas do Visual Studio para Contêineres e o Docker for Windows
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: bcc30ec13096b37d7540c187d11c846d6c575093
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179920"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Início Rápido: Usar o Docker com um aplicativo de página única do React no Visual Studio

Com o Visual Studio, você pode criar, depurar e executar aplicativos do ASP.NET Core facilmente em contêineres, incluindo aqueles com aplicativo de página única do React.js, e publicá-los no ACR (Registro de Contêiner do Azure), no Docker Hub, no Serviço de Aplicativo do Azure ou no seu próprio registro de contêiner. Neste artigo, publicaremos no ACR.

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) com as workloads **Desenvolvimento para a Web**, **Ferramentas do Azure** e/ou **Desenvolvimento multiplataforma do .NET Core** instaladas
* Para publicar no Registro de Contêiner do Azure, uma assinatura do Azure. [Inscreva-se para uma avaliação gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com **Desenvolvimento para a Web**, a carga de trabalho de **Ferramentas do Azure** e/ou **Desenvolvimento multiplataforma do .NET Core** instalados
* [Ferramentas de desenvolvimento do .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) para o desenvolvimento com .NET Core 2.2
* Para publicar no Registro de Contêiner do Azure, uma assinatura do Azure. [Inscreva-se para uma avaliação gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).
::: moniker-end

## <a name="installation-and-setup"></a>Instalação e configuração

Para a instalação do Docker, primeiro examine as informações em [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker Desktop for Windows: o que saber antes de instalar). Em seguida, instale o [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Criar um projeto e adicionar suporte ao Docker

::: moniker range="vs-2017"
1. Clique em um novo projeto, usando o modelo do **Aplicativo Web ASP.NET Core**.
1. Selecione **React.js**. Não é possível selecionar **Habilitar suporte ao Docker**, mas não se preocupe, você pode adicionar esse suporte depois de criar o projeto.

   ![Captura de tela do novo projeto React.js](media/container-tools-react/vs2017/new-react-project.png)

1. Clique com botão direito do mouse no nó do projeto e escolha **Adicionar**>**Suporte ao Docker** para adicionar um Dockerfile ao seu projeto.

   ![Adicionar suporte ao Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Selecione o tipo de contêiner do Linux e, em seguida, clique em **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Clique em um novo projeto, usando o modelo do **Aplicativo Web ASP.NET Core**.
1. Selecione **React.js**e clique em **Criar**. Não é possível selecionar **Habilitar suporte ao Docker**, mas não se preocupe, você pode adicionar esse suporte depois.

   ![Captura de tela do novo projeto React.js](media/container-tools-react/vs2019/new-react-project.png)

1. Clique com botão direito do mouse no nó do projeto e escolha **Adicionar**>**Suporte ao Docker** para adicionar um Dockerfile ao seu projeto.

   ![Adicionar suporte ao Docker](media/container-tools-react/vs2017/add-docker-support.png)

1. Selecione o Linux como o tipo de contêiner.
::: moniker-end

## <a name="dockerfile-overview"></a>Visão geral do Dockerfile

Um *Dockerfile*, ou seja, a receita para criar uma imagem final do Docker, é criado no projeto. Consulte [Referência do Dockerfile](https://docs.docker.com/engine/reference/builder/) para compreender seus comandos.

Abra o *Dockerfile* no projeto e adicione as linhas a seguir para instalar o Node.js 10.x no contêiner. Certifique-se de adicionar essas linhas na primeira seção, para adicionar a instalação de *npm.exe* do Gerenciador de pacotes do nó à imagem base usada nas etapas subsequentes.

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

O *Dockerfile* deve se parecer com o seguinte:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

O *Dockerfile* anterior baseia-se na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e inclui instruções para modificar a imagem base criando o projeto e adicionando-o ao contêiner.

Quando a caixa de seleção **Configurar para HTTPS** do novo projeto estiver marcada, o *Dockerfile* exibirá duas portas. Uma porta é usada para o tráfego HTTP; a outra porta é usada para o HTTPS. Se a caixa de seleção não estiver marcada, uma única porta (80) será exposta para o tráfego HTTP.

## <a name="debug"></a>Depurar

Selecione **Docker** no menu suspenso de depuração na barra de ferramentas e inicie a depuração do aplicativo. Poderá aparecer uma mensagem com um aviso sobre a confiança em um certificado, escolha confiar no certificado para continuar.

A opção **Ferramentas de Contêiner** na janela **Saída** mostra quais ações estão ocorrendo. Você deve ver as etapas de instalação associadas a *npm.exe*.

O navegador mostra a página inicial do aplicativo.

::: moniker range="vs-2017"
   ![Captura de tela do aplicativo em execução](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Captura de tela do aplicativo em execução](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Tente navegar até a página *Contador* e teste o código do contador no lado do cliente clicando no botão **Incremento**.

Abra o **PMC** (console do gerenciador de pacotes) no menu **Ferramentas**> Gerenciador de Pacotes NuGet, **Console do Gerenciador de Pacotes**.

A imagem resultante do Docker do aplicativo é marcada como *dev*. A imagem é baseada na marcação *2.2-aspnetcore-runtime* da imagem base de *microsoft/dotnet*. Execute o comando `docker images` na janela do PMC **(Console do Gerenciador de Pacotes)** . As imagens no computador são exibidas:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> A imagem **dev** não contém os binários do aplicativo e outros tipos de conteúdo, pois as configurações de **depuração** usam montagem de volume para fornecer a experiência iterativa de edição e depuração. Para criar uma imagem de produção que contém todo o conteúdo, use a configuração de **Versão**.

Execute o comando `docker ps` no PMC. Observe que o aplicativo está em execução usando o contêiner:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Publicar imagens do Docker

Depois que o ciclo de desenvolvimento e de depuração do aplicativo forem concluídos, você poderá criar uma imagem de produção do aplicativo.

1. Altere a lista suspensa de configuração para **Versão** e compile o aplicativo.
1. Clique com o botão direito no projeto em **Gerenciador de Soluções** e escolha **Publicar**.
1. Na caixa de diálogo de destino de publicação, selecione a guia **Registro de Contêiner**.
1. Escolha **Criar Registro de Contêiner do Azure** e clique em **Publicar**.
1. Preencha os valores desejados em **Criar um novo Registro de Contêiner do Azure**.

    | Configuração      | Valor sugerido  | DESCRIÇÃO                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefixo DNS** | Nome globalmente exclusivo | Nome que identifica exclusivamente o registro de contêiner. |
    | **Assinatura** | Escolha sua assinatura | A assinatura do Azure a utilizar. |
    | **[Grupo de Recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome do grupo de recursos no qual criar o registro de contêiner. Escolha **Novo** para criar um novo grupo de recursos.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Padrão | Camada de serviço do registro de contêiner  |
    | **Local do Registro** | Um local próximo | Escolha um Local em uma [região](https://azure.microsoft.com/regions/) próxima a você ou perto de outros serviços que usarão o registro de contêiner. |

    ![Caixa de diálogo Criar um Registro de Contêiner do Azure do Visual Studio][0]

1. Clique em **Criar**.

   ![Captura de tela mostrando a publicação bem-sucedida](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Próximas etapas

Agora, é possível extrair o contêiner do registro para qualquer host capaz de executar imagens do Docker, por exemplo [Instâncias de Contêiner do Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Recursos adicionais

* [Desenvolvimento de contêiner com o Visual Studio](/visualstudio/containers)
* [Solucionar problemas de desenvolvimento do Visual Studio com o Docker](troubleshooting-docker-errors.md)
* [Repositório do GitHub e Ferramentas do Visual Studio para Contêineres](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end