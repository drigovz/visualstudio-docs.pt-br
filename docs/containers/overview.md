---
title: Ferramentas de contêiner do Visual Studio no Windows
description: Conheça as ferramentas disponíveis no Visual Studio para trabalhar com o Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 4b03ccddadf954b8430b7ad9b5a4ed765fccc3f5
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59538054"
---
# <a name="container-tools-in-visual-studio"></a>Ferramentas de contêiner no Visual Studio

As ferramentas incluídas no Visual Studio para desenvolvimento com os contêineres são fáceis de usar e simplificam muito a criação, depuração e implantação de aplicativos em contêineres. Você pode trabalhar com um contêiner em um único projeto ou pode usar a orquestração de contêiner com o Docker Compose, Service Fabric ou Kubernetes para trabalhar com vários serviços em contêineres.

> [!NOTE]
> Este artigo se aplica ao Visual Studio para Windows e não ao Visual Studio para Mac.

> [!TIP]
> Para saber mais sobre como instalar o Docker for Windows, confira [Área de trabalho do Docker for Windows](https://docs.docker.com/docker-for-windows/).

## <a name="docker-support-in-visual-studio"></a>Suporte ao Docker no Visual Studio

O suporte ao Docker está disponível em alguns tipos de projeto do .NET.  Ele está disponível para projetos do ASP.NET, do ASP.NET Core e projetos de console .NET Core e .NET Framework.

O suporte ao Docker no Visual Studio foi alterado ao longo das versões em resposta às necessidades dos clientes. Há dois níveis de suporte do Docker que você pode adicionar a um projeto, e as opções com suporte variam conforme o tipo de projeto e a versão do Visual Studio. Com alguns tipos de projeto com suporte, adicione o suporte do Docker se você quiser apenas um contêiner para um único projeto, sem o uso de orquestração.  O próximo nível é o suporte à orquestração de contêiner, que adiciona os arquivos de suporte apropriados para o orquestrador específico que você escolher.  

::: moniker range="vs-2017"

Com o Visual Studio 2017, você pode usar o Docker Compose e o Service Fabric como serviços de orquestração de contêiner.  Também é possível usar Kubernetes, se instalar as [Ferramentas do Visual Studio para Kubernetes](https://aka.ms/get-vsk8stools).

> [!NOTE]
> Se você estiver usando uma versão do Visual Studio 2017 anterior à 15.8 ou um modelo de projeto do .NET Framework (não o .NET Core), ao adicionar o suporte do Docker, o suporte à orquestração usando o Docker Compose é adicionado automaticamente. O suporte à orquestração de contêiner, por meio do Docker Compose, é adicionado automaticamente no Visual Studio 2017 versões 15.0 a 15.7 e em projetos do .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

Com o Visual Studio 2019, você pode usar o Docker Compose, o Kubernetes e o Service Fabric como serviços de orquestração de contêiner.

> [!NOTE]
> Se você estiver usando o modelo de projeto completo de console do .NET Framework, ao adicionar suporte ao Docker, o suporte à orquestração usando o Docker Compose é adicionado automaticamente.
::: moniker-end

Os comandos **Adicionar > Suporte ao Docker** e **Adicionar > Suporte ao orquestrador de contêiner** estão localizados no menu de clique com o botão direito (ou menu de contexto) do nó do projeto para um projeto do ASP.NET Core no **Gerenciador de Soluções**, como mostrado na captura de tela a seguir:

![Adicionar a opção de menu de Suporte ao Docker no Visual Studio](./media/overview/add-docker-support-menu.png)

### <a name="adding-docker-support-without-orchestration"></a>Adição de suporte ao Docker (sem a orquestração)

Para adicionar suporte ao Docker para um projeto existente, selecione **Adicionar** > **Suporte ao Docker** em **Gerenciador de Soluções**. Também é possível habilitar o suporte ao Docker durante a criação do projeto selecionando **Habilitar suporte ao Docker** ao criar um novo projeto, como mostrado na captura de tela a seguir:

::: moniker range="vs-2017"
![Habilitar o suporte ao Docker para o novo aplicativo Web do ASP.NET Core no Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Habilitar o suporte ao Docker para o novo aplicativo Web do ASP.NET Core no Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

Ao adicionar ou habilitar o suporte ao Docker, o Visual Studio adiciona o seguinte ao projeto:

- um arquivo *Dockerfile*
- um arquivo .dockerignore
- uma referência de pacote do NuGet para o Microsoft.VisualStudio.Azure.Containers.Tools.Targets

::: moniker range=">=vs-2019"
A solução tem esta aparência depois de adicionar o suporte ao Docker:

![Captura de tela do Gerenciador de Soluções com o Dockerfile e o arquivo .dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Ao habilitar o suporte ao Docker durante a criação do projeto em um projeto do ASP.NET (.NET Framework, não em um projeto do .NET Core), como mostrado na captura de tela a seguir, o suporte à orquestração de contêiner também é adicionado.

![Habilitar o suporte ao Docker Compose para um projeto do ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Suporte ao Docker Compose

Se você deseja compor uma solução de vários contêiner usando o Docker Compose, adicione o suporte à orquestração de contêiner aos seus projetos. Isso permite que você execute e depure um grupo de contêineres (uma solução inteira ou um grupo de projetos) ao mesmo tempo se eles estiverem definidos no mesmo arquivo *docker-compose.yml*.

Para adicionar o suporte à orquestração de contêiner usando o Docker Compose, clique com o botão direito no nó do projeto ou na solução no **Gerenciador de Soluções** e escolha **Adicionar > Suporte à orquestração de contêiner**. Em seguida, escolha **Docker Compose** para gerenciar os contêineres.

Depois de adicionar o suporte à orquestração de contêiner ao seu projeto, você verá um *Dockerfile* adicionado ao projeto (se já não houver um lá) e uma pasta **docker-compose** adicionada à solução no **Gerenciador de Soluções**, como mostrado aqui:

![Arquivos do Docker no Gerenciador de Soluções no Visual Studio](media/overview/docker-support-solution-explorer.png)

Se o *docker-compose.yml* já existir, o Visual Studio adiciona nele apenas as linhas necessárias do código de configuração.

Repita o processo com os outros projetos que você deseja controlar usando o Docker Compose.

## <a name="kubernetes-support"></a>Suporte a Kubernetes

::: moniker range="vs-2017"
Para adicionar o suporte a Kubernetes, instale as [Ferramentas do Visual Studio para Kubernetes](https://aka.ms/get-vsk8stools).
::: moniker-end

Com suporte a Kubernetes, você pode habilitar uma conexão entre seu projeto local e um cluster do Kubernetes em execução no [Serviço de Kubernetes do Azure (AKS)](/azure/aks) e, portanto, modificar e depurar seus serviços em execução no AKS usando o Visual Studio.  Esse serviço é fornecido pelo [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). O Azure Dev Spaces também possibilita que você configure ramificações separadas dos seus serviços Kubernetes chamados *espaços de desenvolvimento* para fins de desenvolvimento, portanto, você pode isolar com eficiência os serviços de produção das versões de trabalho em desenvolvimento e manter as modificações distintas claramente separadas entre si.

Para adicionar suporte a Kubernetes aos seus projetos, escolha **Kubernetes/Helm** ao adicionar o suporte à orquestração de contêiner. Vários arquivos são adicionados ao seu projeto, incluindo *azds.yaml*, que configura os Azure Dev Spaces e os gráficos do Helm que descrevem a estrutura dos seus serviços Kubernetes.

## <a name="service-fabric-support"></a>Suporte ao Service Fabric

Com as ferramentas do Service Fabric no Visual Studio, você pode desenvolver e depurar no Azure Service Fabric, executar e depurar localmente, e implantar no Azure.

::: moniker range="vs-2017"
O Visual Studio 2017 versão 15.9 e posteriores com a carga de trabalho de desenvolvimento do Azure instalada oferece suporte ao desenvolvimento de microsserviços em contêineres usando os contêineres do Windows e a orquestração do Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
O Visual Studio 2019 oferece suporte ao desenvolvimento de microsserviços em contêineres usando os contêineres do Windows e a orquestração do Service Fabric.
::: moniker-end

Para obter um tutorial detalhado, confira [Tutorial: implantar um aplicativo .NET em um contêiner do Windows no Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Para obter mais informações sobre o Azure Service Fabric, confira o [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Integração contínua e implantação contínua (CI/CD)

O Visual Studio conecta-se prontamente com o Azure Pipelines para integração contínua e automatizada e para a entrega de alterações na configuração e código de serviço. Para iniciar, confira [Criar seu primeiro pipeline](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Para o Service Fabric, confira [Tutorial: implantar seu aplicativo ASP.NET Core no Azure Service Fabric usando o Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Para Kubernetes, confira [Implantar um aplicativo de contêiner do Docker no Serviço de Kubernetes do Azure](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Próximas etapas

Para obter mais detalhes sobre os serviços de implementação e uso de ferramentas do Visual Studio para trabalhar com contêineres, leia os seguintes artigos:

[Depurando aplicativos em um contêiner local do Docker](vs-azure-tools-docker-edit-and-refresh.md)

[Implantar um contêiner ASP.NET em um registro de contêiner usando o Visual Studio](vs-azure-tools-docker-hosting-web-apps-in-docker.md)
