---
title: Ferramentas visuais do estúdio para Docker com ASP.NET
author: ghogen
description: Saiba como usar as ferramentas do Visual Studio 2019 e do Docker para Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: d6d519483b350f2c1086c76bc17522b71a435fe9
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389990"
---
Com o Visual Studio, você pode facilmente construir, depurar e executar aplicativos .NET, ASP.NET e ASP.NET Core e publicá-los no Azure Container Registry (ACR), Docker Hub, Azure App Service ou no seu próprio registro de contêineres. Neste artigo, publicaremos um aplicativo ASP.NET Core para a ACR.

## <a name="prerequisites"></a>Pré-requisitos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com **Desenvolvimento para a Web**, a carga de trabalho de **Ferramentas do Azure** e/ou **Desenvolvimento multiplataforma do .NET Core** instalados
* [.NET Core Development Tools](https://dotnet.microsoft.com/download/dotnet-core/) para desenvolvimento com .NET Core
* Para publicar no Registro de Contêiner do Azure, uma assinatura do Azure. [Inscreva-se para um teste gratuito](https://azure.microsoft.com/free/dotnet/).

## <a name="installation-and-setup"></a>Instalação e configuração

Para a instalação do Docker, primeiro revise as informações no [Docker Desktop para Windows: O que saber antes de instalar](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Em seguida, instale o [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Adicionar um projeto a um contêiner do Docker

1. Crie um novo projeto usando o modelo **de aplicativo da Web ASP.NET** ou se você quiser usar o .NET Framework em vez de .NET Core, escolha ASP.NET Aplicativo Web **(.NET Framework)**.
1. Selecione **o aplicativo da Web**e certifique-se de que a caixa de seleção Ativar suporte do **Docker** esteja selecionada.

   ![Caixa de seleção Habilitar Suporte do Docker](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   A captura de tela mostra .NET Core; se você estiver usando .NET Framework, parece um pouco diferente.

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

O *Dockerfile* anterior baseia-se na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e inclui instruções para modificar a imagem base criando o projeto e adicionando-o ao contêiner. Se você estiver usando o Quadro .NET, a imagem base será diferente.

Quando a caixa de seleção **Configurar para HTTPS** do novo projeto estiver marcada, o *Dockerfile* exibirá duas portas. Uma porta é usada para o tráfego HTTP; a outra porta é usada para o HTTPS. Se a caixa de seleção não estiver marcada, uma única porta (80) será exposta para o tráfego HTTP.

## <a name="debug"></a>Depurar

Selecione **Docker** no menu suspenso de depuração na barra de ferramentas e inicie a depuração do aplicativo. Poderá aparecer uma mensagem com um aviso sobre a confiança em um certificado, escolha confiar no certificado para continuar.

A opção **Ferramentas de Contêiner** na janela **Saída** mostra quais ações estão ocorrendo. Na primeira vez, pode levar um tempo para baixar a imagem base, mas é muito mais rápida em corridas subseqüentes.

>[!NOTE]
> Se você precisar alterar as portas para depuração, você pode fazer isso no arquivo *launchSettings.json.* Consulte [as configurações de lançamento do contêiner](../../container-launch-settings.md).

## <a name="containers-window"></a>Janela de contêineres

Se você tiver o Visual Studio 2019 versão 16.4 ou posterior, você pode usar a janela **Containers** para visualizar contêineres em execução em sua máquina, bem como imagens que você tem disponíveis.

Abra a janela **Containers** usando a caixa de pesquisa no IDE (pressione **Ctrl**+**Q** para usá-la), digite `container`e escolha a janela **Containers** na lista.

Você pode montar a janela containers em um lugar conveniente, como abaixo do editor, movendo-a e seguindo as **guias** de colocação da janela.

Na janela, encontre seu contêiner e passe por cada guia para visualizar as variáveis do ambiente, mapeamentos de portas, logs e o sistema de arquivos.

![Captura de tela da janela Containers](../../media/overview/vs-2019/container-tools-window.png)

Para obter mais informações, consulte [Ver e diagnosticar recipientes e imagens no Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Publicar imagens do Docker

Depois que o ciclo de desenvolvimento e de depuração do aplicativo forem concluídos, você poderá criar uma imagem de produção do aplicativo.

1. Altere a lista suspensa de configuração para **Versão** e compile o aplicativo.
1. Clique com o botão direito no projeto em **Gerenciador de Soluções** e escolha **Publicar**.
1. Na caixa de diálogo de destino de publicação, selecione a guia **Registro de Contêiner**.
1. Escolha **Criar Registro de Contêiner do Azure** e clique em **Publicar**.
1. Preencha os valores desejados em **Criar um novo Registro de Contêiner do Azure**.

    | Configuração      | Valor sugerido  | Descrição                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefixo DNS** | Nome globalmente exclusivo | Nome que identifica exclusivamente o registro de contêiner. |
    | **Assinatura** | Escolha sua assinatura | A assinatura do Azure a utilizar. |
    | **[Grupo de Recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nome do grupo de recursos no qual criar o registro de contêiner. Escolha **Novo** para criar um novo grupo de recursos.|
    | **[Sku](/azure/container-registry/container-registry-skus)** | Standard | Camada de serviço do registro de contêiner  |
    | **Localização do Registro** | Um local próximo | Escolha um Local em uma [região](https://azure.microsoft.com/regions/) próxima a você ou perto de outros serviços que usarão o registro de contêiner. |

    ![Caixa de diálogo Criar um Registro de Contêiner do Azure do Visual Studio][0]

1. Clique em **Criar**

   ![Captura de tela mostrando a publicação bem-sucedida](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Próximas etapas

Agora, é possível extrair o contêiner do registro para qualquer host capaz de executar imagens do Docker, por exemplo [Instâncias de Contêiner do Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
