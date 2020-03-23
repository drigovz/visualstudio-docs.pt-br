---
title: Tutorial de ferramentas kubernetes | Microsoft Docs
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: f5868f97301eba62d16ea68cdaa0c97c8e20edd1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916957"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Comece com o Visual Studio Kubernetes Tools

As Ferramentas Visual Studio Kubernetes ajudam a agilizar o desenvolvimento de aplicativos contêineres direcionados ao Kubernetes. O Visual Studio pode criar automaticamente os arquivos de configuração como código necessários para suportar a implantação do Kubernetes, como dockerfiles e gráficos Helm. Você pode depurar seu código em um cluster azure Kubernetes Service (AKS) ao vivo usando a Azure Dev Spaces ou publicar diretamente em um cluster AKS de dentro do Visual Studio.

Este tutorial abrange o uso do Visual Studio para adicionar suporte kubernetes a um projeto e publicar para aKS. Se você estiver interessado principalmente em usar [o Azure Dev Spaces](/azure/dev-spaces/) para depurar e testar seu projeto em execução em AKS, você pode pular para o [tutorial do Azure Dev Spaces.](/azure/dev-spaces/get-started-netcore-visualstudio)

## <a name="prerequisites"></a>Pré-requisitos

Para aproveitar essa nova funcionalidade, você precisará:

::: moniker range="vs-2017"
- A versão mais recente do [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) com a *carga de trabalho de ASP.NET e desenvolvimento web.*
- As [ferramentas Kubernetes para Visual Studio,](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)disponíveis como download separado.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com a carga de trabalho de *desenvolvimento Web e do ASP.NET*.
::: moniker-end
- [O Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) instalado em sua estação de trabalho de desenvolvimento (ou seja, onde você executa o Visual Studio), se você deseja construir imagens docker, depurar contêineres Docker em execução local ou publicar para AKS. (O Docker *não* é necessário para construir e depurar contêineres Docker em AKS usando a Azure Dev Spaces.)
::: moniker range="vs-2017"
- Se você deseja publicar para a AKS do Visual Studio *(não* é necessário para depuração em AKS usando Espaços Azure Dev):

    1. As [ferramentas de publicação da AKS,](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)disponíveis como download separado.

    1. Um cluster do Serviço de Kubernetes do Azure. Para obter mais informações, consulte [Criando um cluster AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Certifique-se de [se conectar ao cluster a](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) partir de sua estação de trabalho de desenvolvimento.

    1. Helm CLI instalado em sua estação de trabalho de desenvolvimento. Para obter mais informações, consulte [Installing Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1. O leme configurado contra o `helm init` cluster AKS usando o comando. Para obter mais informações sobre como fazer isso, consulte [Como configurar o Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Crie um novo projeto Kubernetes

::: moniker range="vs-2017"

Depois de ter as ferramentas apropriadas instaladas, inicie o Visual Studio e crie um novo projeto. Em **Nuvem,** escolha o aplicativo de contêiner para o tipo de projeto **Kubernetes.** Selecione este tipo de projeto e escolha **OK**.

![Captura de tela da criação de um novo projeto de aplicativo Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Na janela de início do Visual Studio, procure por *Kubernetes*e escolha o **Aplicativo de Contêiner para Kubernetes**.

![Captura de tela da criação de um novo projeto de aplicativo Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Forneça o nome do projeto.

![Captura de tela da criação de um novo projeto de aplicativo Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Em seguida, você pode escolher qual tipo de ASP.NET aplicativo web Core criar. Escolha **Aplicativo Web**. A opção usual **de suporte ao Docker** não aparece nesta caixa de diálogo.  O suporte ao Docker é habilitado por padrão para um aplicativo de contêiner para Kubernetes.

::: moniker range="vs-2017"

![Captura de tela da seleção de aplicativos web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Captura de tela da seleção de aplicativos web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Adicionar suporte kubernetes a um projeto existente

Alternativamente, você pode adicionar suporte ao Kubernetes a um projeto de aplicativo web ASP.NET Core existente. Para isso, clique com o botão direito do mouse no projeto e escolha **Adicionar** > **suporte ao Orquestrador de Contêineres**.

::: moniker range="vs-2017"

![Captura de tela do item do menu Adicionar adicionado ortodo orquestrador](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Captura de tela do item do menu Adicionar adicionado ortodo orquestrador](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

Na caixa de diálogo, selecione **Kubernetes/Helm** e escolha **OK**.

![Captura de tela da caixa de diálogo Adicionar adicionado orquestrão](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>O que o Visual Studio cria para você

Depois de criar um novo aplicativo de contêiner para o projeto **Kubernetes** ou adicionar suporte a um projeto de orquestrador de contêineres kubernetes a um projeto existente, você verá alguns arquivos adicionais em seu projeto que facilitam a implantação no Kubernetes.

::: moniker range="vs-2017"

![Captura de tela do Solution Explorer depois de adicionar suporte ao Container Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Captura de tela do Solution Explorer depois de adicionar suporte ao Container Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Os arquivos adicionados são:

- um Arquivo Docker, que permite gerar uma imagem de contêiner Docker hospedando este aplicativo web. Como você verá, a ferramenta Visual Studio aproveita este Arquivo Docker ao depurar e implantar no Kubernetes. Se você preferir trabalhar diretamente com a imagem do Docker, clique com o botão direito do mouse no arquivo Docker e escolha **Build Docker Image**.

   ![Captura de tela da opção Build Docker Image](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- um gráfico helm, e uma pasta *de gráficos.* Esses arquivos de inhame compõem o gráfico Helm para o aplicativo, que você pode usar para implantá-lo em Kubernetes. Para obter mais informações [https://www.helm.sh](https://www.helm.sh)sobre Helm, consulte .

- *azds.yaml*. Isso contém configurações para Azure Dev Spaces, que fornece uma experiência rápida e iterativa de depuração no Azure Kubernetes Service. Para obter mais informações, consulte [a documentação do Azure Dev Spaces](/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publique para o Azure Kubernetes Service (AKS)

Com todos esses arquivos no lugar, você pode usar o Visual Studio IDE para escrever e depurar seu código de aplicativo, como você sempre tem. Você também pode usar [o Azure Dev Spaces](/azure/dev-spaces/) para executar e depurar rapidamente seu código em execução ao vivo em um cluster AKS. Para obter mais informações, consulte o [tutorial do Azure Dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio)

Uma vez que você tenha seu código funcionando do jeito que você quer, você pode publicar diretamente do Visual Studio para um cluster AKS.

Para fazer isso, primeiro você precisa verificar duas vezes se você instalou tudo conforme descrito na seção [Pré-requisitos](#prerequisites) o item para publicação no AKS, e executar todas as etapas da linha de comando dadas nos links. Em seguida, configure um perfil de publicação que publique sua imagem de contêiner no Azure Container Registry (ACR). Em seguida, o AKS pode puxar a imagem do contêiner do ACR e implantá-la no cluster.

1. No **Solution Explorer,** clique com o botão direito do mouse no *seu projeto* e escolha **Publicar**.

   ![Captura de tela do item do menu Publicar](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Na tela **Publicar,** escolha **Registro de contêiner** como alvo de publicação e siga as instruções para selecionar o registro do contêiner. Se você ainda não tiver um registro de contêiner, escolha **Criar novo registro de contêiner do Azure** para criar um no Visual Studio. Para obter mais informações, consulte [Publique seu contêiner no Registro de Contêineres do Azure](hosting-web-apps-in-docker.md).

   ![Captura de tela de Pick a publish target screen](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. De volta ao Solution Explorer, clique com o botão direito do mouse na sua *solução* e clique **em Publicar para a Azure AKS**.

   ![Captura de tela do item do menu Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Escolha sua assinatura e seu cluster AKS, juntamente com o perfil de publicação aCR que você acabou de criar. Em seguida, clique em **OK**.

   ![Captura de tela de Publicar para tela AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Isso leva você à tela **Publish to Azure AKS.**

5. Escolha o link **Configurar Leme** para atualizar a linha de comando usada para instalar os gráficos Helm no servidor.

   ![Captura de tela do link Configurar Helm](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Atualizar a linha de comando é útil se houver argumentos de linha de comando personalizados que você deseja especificar, como um contexto kubernetes diferente ou nome de gráfico.

   ![Captura de tela do Helm configurar tela](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Quando estiver pronto para implantar, clique no botão **Publicar** para publicar seu aplicativo no AKS.

   ![Captura de tela de publicar na tela do Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Parabéns! Agora você pode usar todo o poder do Visual Studio para todo o desenvolvimento do seu aplicativo Kubernetes.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre o desenvolvimento do Kubernetes no Azure lendo a [documentação aks](/azure/aks).

Saiba mais sobre os Espaços de Dev do Azure lendo a documentação do [Azure Dev Spaces](/azure/dev-spaces/)
