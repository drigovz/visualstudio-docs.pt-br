---
title: Usar o Bridge para kubernetes com o Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Saiba como usar o Bridge para kubernetes com o Visual Studio para conectar seu computador de desenvolvimento a um cluster kubernetes
keywords: Ponte para kubernetes, Azure Dev Spaces, espaços de desenvolvimento, Docker, kubernetes, Azure, contêineres
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: c7d046ca63af5aa65f5cd286e9a6199afc6c2947
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845834"
---
# <a name="use-bridge-to-kubernetes"></a>Usar ponte para kubernetes

Você pode usar o Bridge para kubernetes para redirecionar o tráfego entre o cluster do kubernetes e o código em execução no seu computador de desenvolvimento. Este guia também fornece um script para implantar um aplicativo de exemplo grande com vários microserviços em um cluster kubernetes.

## <a name="before-you-begin"></a>Antes de começar

Este guia usa o [aplicativo de exemplo de compartilhamento de bicicletas][bike-sharing-github] para demonstrar como conectar seu computador de desenvolvimento a um cluster kubernetes. Se você já tiver seu próprio aplicativo em execução em um cluster kubernetes, ainda poderá seguir as etapas abaixo e usar os nomes dos seus próprios serviços.

### <a name="prerequisites"></a>Pré-requisitos

* Uma assinatura do Azure. Caso não tenha uma assinatura do Azure, é possível criar uma [conta gratuita](https://azure.microsoft.com/free).
* A [CLI do Azure][azure-cli] instalada.
* [Visual Studio 2019][visual-studio] versão 16,7 Preview 4 ou superior em execução no Windows 10 com a carga de trabalho de *desenvolvimento do Azure* instalada.
* [Ponte para a extensão kubernetes instalada][btk-extension].

Além disso, para aplicativos de console do .NET, instale o pacote NuGet *Microsoft. VisualStudio. Azure. kubernetes. Tools. targets* .

## <a name="create-a-kubernetes-cluster"></a>Criar um cluster do Kubernetes

Crie um cluster AKS em uma [região com suporte][supported-regions]. Os comandos a seguir criam um grupo de recursos chamado *MyResourceGroup* e um cluster do AKS chamado *MyAKS*.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Instalar o aplicativo de exemplo

Instale o aplicativo de exemplo no cluster usando o script fornecido. Você pode executar esse script usando o [Azure cloud Shell][azure-cloud-shell].

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Navegue até o aplicativo de exemplo que executa o cluster abrindo sua URL pública, que é exibida na saída do script de instalação.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

No exemplo acima, a URL pública é `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` .

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Conectar-se ao cluster e depurar um serviço

No computador de desenvolvimento, baixe e configure a CLI do kubernetes para se conectar ao cluster do kubernetes usando [AZ AKs Get-Credentials][az-aks-get-credentials].

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

No repositório de [aplicativos de exemplo de compartilhamento de bicicletas][bike-sharing-github] no GitHub, use a lista suspensa no botão **código** verde e escolha **abrir no Visual Studio** para clonar o repositório localmente e abrir a pasta no Visual Studio. Em seguida, use **arquivo**  >  **Abrir projeto** para abrir o projeto **app. csproj** na *pasta Samples/BikeSharingApp/ReservationEngine* .

Em seu projeto, selecione **ponte para kubernetes** na lista suspensa configurações de inicialização, conforme mostrado abaixo.

![Escolha ponte para kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Clique no botão iniciar ao lado de *ponte para kubernetes*. Na caixa de diálogo **Criar perfil para a ponte para o kubernetes** :

* Selecione sua assinatura.
* Selecione *MyAKS* para o cluster.
* Selecione *bikeapp* para seu namespace.
* Selecione *reservationengine* para o serviço redirecionar.
* Selecione *aplicativo* para o perfil de inicialização.
* Selecione `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` para a URL para iniciar o navegador.

![Escolha a ponte para o cluster kubernetes](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Você só pode redirecionar os serviços que têm um único Pod.

Escolha se deseja ou não ser executado de forma isolada, o que significa que outras pessoas que estão usando o cluster não serão afetadas pelas suas alterações. Esse modo de isolamento é realizado roteando suas solicitações para a cópia de cada serviço afetado, mas roteando todos os outros tráfego normalmente. Mais explicações sobre como isso é feito pode ser encontrado em [como a ponte para o kubernetes funciona][btk-overview-routing].

Clique em **salvar e inicie a depuração**.

Todo o tráfego no cluster kubernetes é redirecionado para o serviço *reservationengine* para a versão do seu aplicativo em execução no seu computador de desenvolvimento. A ponte para o kubernetes também roteia todo o tráfego de saída do aplicativo de volta para o cluster kubernetes.

> [!NOTE]
> Você receberá uma solicitação para permitir que o *EndpointManager* seja executado com privilégios elevados e modificará o arquivo de hosts.

Seu computador de desenvolvimento está conectado quando a barra de status mostra que você está conectado ao `reservationengine` serviço.

![Computador de desenvolvimento conectado](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Em inicializações subsequentes, você não será avisado com a caixa de diálogo **Criar perfil para a ponte para kubernetes** . Você atualiza essas configurações na **depuração** nas propriedades do projeto.

Quando o computador de desenvolvimento estiver conectado, o tráfego começará a redirecionar para o seu computador de desenvolvimento para o serviço que você está substituindo.

## <a name="set-a-break-point"></a>Definir um ponto de interrupção

Abra [BikesHelper.cs][bikeshelper-cs-breakpoint] e clique em algum lugar na linha 26 para colocar o cursor lá. Defina um ponto de interrupção pressionando *F9* ou selecionando **depurar**  >  **alternância de ponto de interrupção**.

Navegue até o aplicativo de exemplo abrindo a URL pública. Selecione **Aurelia Briggs (cliente)** como o usuário e, em seguida, selecione uma bicicleta para alugar. Escolha a **bicicleta de aluguel**. Retorne ao Visual Studio e observe que a linha 26 está realçada. O ponto de interrupção que você definiu pausou o serviço na linha 26. Para retomar o serviço, pressione **F5** ou clique em **depurar**  >  **continuar**. Retorne ao seu navegador e verifique se a página mostra que você aluga a bicicleta.

Remova o ponto de interrupção colocando o cursor na linha 26 em `BikesHelper.cs` e pressionando **F9**.

> [!NOTE]
> Por padrão, a interrupção da tarefa de depuração também desconecta o computador de desenvolvimento do cluster kubernetes. Você pode alterar esse comportamento alterando **desconectar após a depuração** para `false` na seção **ferramentas de depuração kubernetes** das opções de depuração. Depois de atualizar essa configuração, o computador de desenvolvimento permanecerá conectado quando você parar e iniciar a depuração. Para desconectar seu computador de desenvolvimento do cluster, clique no botão **Desconectar** na barra de ferramentas.

## <a name="additional-configuration"></a>Configuração adicional

A ponte para kubernetes pode manipular o tráfego de roteamento e replicar variáveis de ambiente sem nenhuma configuração adicional. Se precisar baixar todos os arquivos que são montados no contêiner em seu cluster kubernetes, como um arquivo ConfigMap, você pode criar um `KubernetesLocalProcessConfig.yaml` para baixar esses arquivos em seu computador de desenvolvimento. Para obter mais informações, consulte [usando KubernetesLocalProcessConfig. YAML para configuração adicional com for Bridge para kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Usando log e diagnóstico

Você pode encontrar os logs de diagnóstico no `Bridge to Kubernetes` diretório no diretório *temporário* do seu computador de desenvolvimento. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Remover o aplicativo de exemplo do cluster

Use o script fornecido para remover o aplicativo de exemplo do cluster.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Próximas etapas

Saiba como o Bridge to kubernetes funciona.

> [!div class="nextstepaction"]
> [Como o Bridge to kubernetes funciona](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation