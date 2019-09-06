---
title: Ferramentas do Visual Studio para Docker com ASP.NET Core
author: ghogen
description: Saiba como usar as ferramentas e Docker for Windows do Visual Studio 2019
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 124f60a4a632115625524b4e30ab28f795d41660
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70311981"
---
Com o Visual Studio, você pode facilmente compilar, depurar e executar aplicativos ASP.NET Core em contêineres e publicá-los no ACR (registro de contêiner do Azure), no Hub do Docker, no serviço de Azure App ou em seu próprio registro de contêiner. Neste artigo, publicaremos no ACR.

## <a name="prerequisites"></a>Pré-requisitos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com **Desenvolvimento para a Web**, a carga de trabalho de **Ferramentas do Azure** e/ou **Desenvolvimento multiplataforma do .NET Core** instalados
* [Ferramentas de desenvolvimento do .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) para o desenvolvimento com .NET Core 2.2
* Para publicar no Registro de Contêiner do Azure, uma assinatura do Azure. [Inscreva-se para uma avaliação gratuita](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Instalação e configuração

Para a instalação do Docker, primeiro examine as informações em [Docker Desktop for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker Desktop for Windows: o que saber antes de instalar). Em seguida, instale o [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Adicionar um projeto a um contêiner do Docker

1. Clique em um novo projeto, usando o modelo do **Aplicativo Web ASP.NET Core**.
1. Selecione **aplicativo Web**e verifique se a caixa de seleção **habilitar suporte ao Docker** está marcada.

   ![Caixa de seleção Habilitar Suporte do Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Selecione o tipo de contêiner desejado (Windows ou Linux) e clique em **Criar**.

## <a name="dockerfile-overview"></a>Visão geral do Dockerfile

Um *Dockerfile*, ou seja, a receita para criar uma imagem final do Docker, é criado no projeto. Confira a [referência do Dockerfile](https://docs.docker.com/engine/reference/builder/) para entender os comandos que ele contém:

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

O *Dockerfile* anterior baseia-se na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e inclui instruções para modificar a imagem base criando o projeto e adicionando-o ao contêiner.

Quando a caixa de seleção **Configurar para HTTPS** do novo projeto estiver marcada, o *Dockerfile* exibirá duas portas. Uma porta é usada para o tráfego HTTP; a outra porta é usada para o HTTPS. Se a caixa de seleção não estiver marcada, uma única porta (80) será exposta para o tráfego HTTP.

## <a name="debug"></a>Depurar

Selecione **Docker** no menu suspenso de depuração na barra de ferramentas e inicie a depuração do aplicativo. Poderá aparecer uma mensagem com um aviso sobre a confiança em um certificado, escolha confiar no certificado para continuar.

A opção **Ferramentas de Contêiner** na janela **Saída** mostra quais ações estão ocorrendo.

Abra o **PMC** (console do gerenciador de pacotes) no menu **Ferramentas**> Gerenciador de Pacotes NuGet, **Console do Gerenciador de Pacotes**.

A imagem resultante do Docker do aplicativo é marcada como *dev*. A imagem é baseada na marcação *2.2-aspnetcore-runtime* da imagem base de *microsoft/dotnet*. Execute o comando `docker images` na janela do PMC **(Console do Gerenciador de Pacotes)** . As imagens no computador são exibidas:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> A imagem **dev** não contém os binários do aplicativo e outros tipos de conteúdo, pois as configurações de **depuração** usam montagem de volume para fornecer a experiência iterativa de edição e depuração. Para criar uma imagem de produção que contém todo o conteúdo, use a configuração de **Versão**.

Execute o comando `docker ps` no PMC. Observe que o aplicativo está em execução usando o contêiner:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        hellodockertools:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
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

1. Clique em **Criar**

   ![Captura de tela mostrando a publicação bem-sucedida](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Próximas etapas

Agora, é possível extrair o contêiner do registro para qualquer host capaz de executar imagens do Docker, por exemplo [Instâncias de Contêiner do Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
