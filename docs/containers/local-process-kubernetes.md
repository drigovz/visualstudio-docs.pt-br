---
title: Usar o processo local com o kubernetes com o Visual Studio (visualização)
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Saiba como usar o processo local com o kubernetes com o Visual Studio para conectar seu computador de desenvolvimento a um cluster kubernetes
keywords: Processo local com kubernetes, Azure Dev Spaces, espaços de desenvolvimento, Docker, kubernetes, Azure, contêineres
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 191fd1df377bd15d78c329b88d20f1fed8669663
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913273"
---
# <a name="use-local-process-with-kubernetes-preview"></a>Usar processo local com kubernetes (versão prévia)

O processo local com o kubernetes permite que você execute e depure o código em seu computador de desenvolvimento, enquanto ainda está conectado ao cluster kubernetes com o restante do seu aplicativo ou serviços. Por exemplo, se você tiver uma grande arquitetura de microserviços com muitos bancos de dados e serviços interdependentes, é difícil replicar essas dependências no seu computador de desenvolvimento. Além disso, a criação e a implantação de código em seu cluster kubernetes para cada alteração de código durante o desenvolvimento de loop interno podem ser lentas, demoradas e difíceis de usar com um depurador.

O processo local com kubernetes evita que você precise compilar e implantar seu código no cluster, em vez de criar uma conexão diretamente entre o computador de desenvolvimento e o cluster. Conectar seu computador de desenvolvimento ao cluster durante a depuração permite que você teste e desenvolva rapidamente seu serviço no contexto do aplicativo completo sem criar nenhuma configuração de Docker ou kubernetes.

O processo local com o kubernetes redireciona o tráfego entre o cluster kubernetes conectado e o computador de desenvolvimento. Esse redirecionamento de tráfego permite que o código em seu computador de desenvolvimento e serviços em execução no cluster kubernetes se comuniquem como se estivessem no mesmo cluster kubernetes. O processo local com o kubernetes também fornece uma maneira de replicar as variáveis de ambiente e os volumes montados disponíveis para pods no seu cluster kubernetes em seu computador de desenvolvimento. Fornecer acesso a variáveis de ambiente e volumes montados em seu computador de desenvolvimento permite que você trabalhe rapidamente em seu código sem ter que replicar essas dependências manualmente.

Neste guia, você aprenderá a usar o processo local com kubernetes para redirecionar o tráfego entre o cluster do kubernetes e o código em execução no seu computador de desenvolvimento. Este guia também fornece um script para implantar um aplicativo de exemplo grande com vários microserviços em um cluster kubernetes.

> [!IMPORTANT]
> Esse recurso está atualmente na visualização. As versões prévias são disponibilizadas com a condição de que você concorde com os [termos de uso complementares][preview-terms]. Alguns aspectos desse recurso podem alterar antes da GA (disponibilidade geral).

## <a name="before-you-begin"></a>Antes de começar

Este guia usa o [aplicativo de exemplo de compartilhamento de bicicletas][bike-sharing-github] para demonstrar como conectar seu computador de desenvolvimento a um cluster kubernetes. Se você já tiver seu próprio aplicativo em execução em um cluster kubernetes, ainda poderá seguir as etapas abaixo e usar os nomes dos seus próprios serviços.

### <a name="prerequisites"></a>Pré-requisitos

* Uma assinatura do Azure. Caso não tenha uma assinatura do Azure, é possível criar uma [conta gratuita](https://azure.microsoft.com/free).
* A [CLI do Azure][azure-cli] instalada.
* [Visual Studio 2019][visual-studio] versão 16,7 Preview 4 ou superior em execução no Windows 10 com a carga de trabalho de *desenvolvimento do Azure* instalada.
* [Processo local para a extensão kubernetes instalada][lpk-extension].

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
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

Navegue até o aplicativo de exemplo que executa o cluster abrindo sua URL pública, que é exibida na saída do script de instalação.

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
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

Abra *mindaro/Samples/BikeSharingApp/ReservationEngine/app. csproj* do [aplicativo de exemplo de compartilhamento de bicicletas][bike-sharing-github] no Visual Studio.

Em seu projeto, selecione *processo local com kubernetes* na lista suspensa configurações de inicialização, conforme mostrado abaixo.

![Escolha o processo local com kubernetes](media/local-process-kubernetes/choose-local-process.png)

Clique no botão iniciar ao lado de *processo local com kubernetes*. Na caixa de diálogo *processo local com kubernetes* :

* Selecione sua assinatura.
* Selecione *MyAKS* para o cluster.
* Selecione *desenvolvimento* para seu namespace.
* Selecione *reservationengine* para o serviço redirecionar.
* Selecione *aplicativo* para o perfil de inicialização.
* Selecione `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` para a URL para iniciar o navegador.

![Escolha o processo local com o cluster kubernetes](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> Você só pode redirecionar os serviços que têm um único Pod.

Clique em *salvar e inicie a depuração*.

Todo o tráfego no cluster kubernetes é redirecionado para o serviço *reservationengine* para a versão do seu aplicativo em execução no seu computador de desenvolvimento. O processo local com kubernetes também roteia todo o tráfego de saída do aplicativo de volta para o cluster kubernetes.

> [!NOTE]
> Você será solicitado a permitir que o *KubernetesDNSManager* execute com privilégios elevados e modifique o arquivo de hosts.

Seu computador de desenvolvimento está conectado quando a barra de status mostra que você está conectado ao serviço *reservationengine* .

![Computador de desenvolvimento conectado](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> No subesquent é iniciado, você não será solicitado com o *processo local com* a caixa de diálogo kubernetes. Você atualiza essas configurações no painel de *depuração* nas propriedades do projeto.

Quando o computador de desenvolvimento estiver conectado, o tráfego começará a redirecionar para o seu computador de desenvolvimento para o serviço que você está substituindo.

## <a name="set-a-break-point"></a>Definir um ponto de interrupção

Abra [BikesHelper.cs][bikeshelper-cs-breakpoint] e clique em algum lugar na linha 26 para colocar o cursor lá. Defina um ponto de interrupção pressionando *F9* ou clicando em *depurar* e, em seguida, *alternar ponto de interrupção*.

Navegue até o aplicativo de exemplo abrindo a URL pública. Selecione *Aurelia Briggs (cliente)* como o usuário e, em seguida, selecione uma bicicleta para alugar. Clique em *bicicleta de aluguel*. Retorne ao Visual Studio e observe que a linha 26 está realçada. O ponto de interrupção que você definiu pausou o serviço na linha 26. Para retomar o serviço, pressione *F5* ou clique em *Depurar* e, em seguida, *Continuar*. Retorne ao seu navegador e verifique se a página mostra que você aluga a bicicleta.

Remova o ponto de interrupção colocando o cursor na linha 26 em `BikesHelper.cs` e pressionando *F9*.

> [!NOTE]
> Por padrão, a interrupção da tarefa de depuração também desconecta o computador de desenvolvimento do cluster kubernetes. Você pode alterar esse comportamento alterando *desconectar após a depuração* para *false* na seção *ferramentas de depuração kubernetes* das opções de depuração. Depois de atualizar essa configuração, o computador de desenvolvimento permanecerá conectado quando você parar e iniciar a depuração. Para desconectar seu computador de desenvolvimento do cluster, clique no botão *Desconectar* na barra de ferramentas.
>
> Se o Visual Studio finalizar abruptamente a conexão com o cluster ou terminar, o serviço que você está redirecionando poderá não ser restaurado para seu estado original antes de você se conectar com o processo local com kubernetes. Para corrigir esse problema, consulte o [Guia de solução de problemas][troubleshooting].

## <a name="additional-configuration"></a>Configuração adicional

O processo local com kubernetes pode manipular o tráfego de roteamento e replicar variáveis de ambiente sem nenhuma configuração adicional. Se precisar baixar todos os arquivos que são montados no contêiner em seu cluster kubernetes, como um arquivo ConfigMap, você pode criar um `KubernetesLocalProcessConfig.yaml` para baixar esses arquivos em seu computador de desenvolvimento. Para obter mais informações, consulte [usando KubernetesLocalProcessConfig. YAML para configuração adicional com o para o processo local com o kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Usando log e diagnóstico

Você pode encontrar os logs de diagnóstico no `Local Process with Kubernetes` diretório no diretório *temporário* do seu computador de desenvolvimento. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Remover o aplicativo de exemplo do cluster

Use o script fornecido para remover o aplicativo de exemplo do cluster.

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Próximas etapas

Saiba como o processo local kubernetes funciona.

> [!div class="nextstepaction"]
> [Como o processo local com Kubernetes funciona](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-local-process-with-kubernetes.md