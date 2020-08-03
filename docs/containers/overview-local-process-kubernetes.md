---
title: Como o processo local com Kubernetes funciona
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Descreve os processos para usar o processo local com o kubernetes para conectar seu computador de desenvolvimento ao cluster kubernetes
keywords: Processo local com kubernetes, Docker, kubernetes, Azure, contêineres
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: f8808da9a2bfd49fb0ee7d661b7e57c776036c1c
ms.sourcegitcommit: e359b93c93c6ca316c0d8b86c2b6e566171fd1ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507879"
---
# <a name="how-local-process-with-kubernetes-works"></a>Como o processo local com Kubernetes funciona

O processo local com o kubernetes permite que você execute e depure o código em seu computador de desenvolvimento, enquanto ainda está conectado ao cluster kubernetes com o restante do seu aplicativo ou serviços. Por exemplo, se você tiver uma grande arquitetura de microserviços com muitos bancos de dados e serviços interdependentes, é difícil replicar essas dependências no seu computador de desenvolvimento. Além disso, a criação e a implantação de código em seu cluster kubernetes para cada alteração de código durante o desenvolvimento de loop interno podem ser lentas, demoradas e difíceis de usar com um depurador.

O processo local com kubernetes evita que você precise compilar e implantar seu código no cluster, em vez de criar uma conexão diretamente entre o computador de desenvolvimento e o cluster. Conectar seu computador de desenvolvimento ao cluster durante a depuração permite que você teste e desenvolva rapidamente seu serviço no contexto do aplicativo completo sem criar nenhuma configuração de Docker ou kubernetes.

O processo local com o kubernetes redireciona o tráfego entre o cluster kubernetes conectado e o computador de desenvolvimento. Esse redirecionamento de tráfego permite que o código em seu computador de desenvolvimento e serviços em execução no cluster kubernetes se comuniquem como se estivessem no mesmo cluster kubernetes. O processo local com o kubernetes também fornece uma maneira de replicar as variáveis de ambiente e os volumes montados disponíveis para pods no seu cluster kubernetes em seu computador de desenvolvimento. Fornecer acesso a variáveis de ambiente e volumes montados em seu computador de desenvolvimento permite que você trabalhe rapidamente em seu código sem ter que replicar essas dependências manualmente.

> [!WARNING]
> O processo local para kubernetes destina-se ao uso somente em cenários de desenvolvimento e teste. Ele não se destina ou tem suporte para uso com clusters de produção ou serviços dinâmicos em uso ativo.

## <a name="using-local-process-with-kubernetes"></a>Usando o processo local com kubernetes

Para usar o processo local com o kubernetes no Visual Studio, você precisa do [visual studio 2019][visual-studio] versão 16,7 Preview 4 ou superior em execução no Windows 10 com a carga de trabalho de *desenvolvimento da web e do ASP.net* instalada e a [extensão de kubernetes de processo local][lpk-extension] instalada. Ao usar o processo local com o kubernetes para estabelecer uma conexão com o cluster do kubernetes, você tem a opção de redirecionar todo o tráfego para e de um pod existente no cluster para seu computador de desenvolvimento.

> [!NOTE]
> Ao usar o processo local com kubernetes, será solicitado que você forneça o nome do serviço para redirecionar para o computador de desenvolvimento. Essa opção é uma maneira conveniente de identificar um pod para redirecionamento. Todo o redirecionamento entre o cluster kubernetes e o computador de desenvolvimento é para um pod.

Quando o processo local com kubernetes estabelece uma conexão com o cluster, ele:

* Solicita que você configure o serviço a ser substituído no cluster, a porta no computador de desenvolvimento a ser usada para seu código e a tarefa de inicialização para seu código como uma ação única.
* Substitui o contêiner no pod no cluster por um contêiner de agente remoto que redireciona o tráfego para o computador de desenvolvimento.
* Executa o [kubectl Port-Forward][kubectl-port-forward] no computador de desenvolvimento para encaminhar o tráfego do seu computador de desenvolvimento para o agente remoto em execução no cluster.
* Coleta informações de ambiente do seu cluster usando o agente remoto. Essas informações de ambiente incluem variáveis de ambiente, serviços visíveis, montagens de volume e montagens secretas.
* Configura o ambiente no Visual Studio para que o serviço no seu computador de desenvolvimento possa acessar as mesmas variáveis como se estivesse em execução no cluster.  
* Atualiza o arquivo de hosts para mapear serviços no cluster para endereços IP locais em seu computador de desenvolvimento. Essas entradas de arquivo de hosts permitem que o código em execução no computador de desenvolvimento faça solicitações a outros serviços em execução no cluster. Para atualizar o arquivo de hosts, o processo local com kubernetes solicitará acesso de administrador em seu computador de desenvolvimento ao se conectar ao cluster.
* Inicia a execução e a depuração do código no computador de desenvolvimento. Se necessário, o processo local com kubernetes liberará as portas necessárias no computador de desenvolvimento, interrompendo os serviços ou processos que estão usando essas portas no momento.

Depois de estabelecer uma conexão com o cluster, você pode executar e depurar o código nativamente em seu computador, sem a Containerização, e o código pode interagir diretamente com o restante do cluster. Qualquer tráfego de rede que o agente remoto recebe é redirecionado para a porta local especificada durante a conexão para que seu código em execução nativamente possa aceitar e processar esse tráfego. As variáveis de ambiente, os volumes e os segredos do seu cluster são disponibilizados para o código em execução no seu computador de desenvolvimento. Além disso, devido às entradas de arquivo de hosts e encaminhamento de porta adicionados ao seu computador de desenvolvedor por processo local com o kubernetes, seu código pode enviar tráfego de rede para serviços em execução no cluster usando os nomes de serviço do cluster e esse tráfego é encaminhado para os serviços em execução no cluster. O tráfego é roteado entre o computador de desenvolvimento e o cluster todo o tempo que você está conectado.

Além disso, o processo local com o kubernetes fornece uma maneira de replicar as variáveis de ambiente e os arquivos montados disponíveis para pods no cluster no seu computador de desenvolvimento por meio do `KubernetesLocalProcessConfig.yaml` arquivo. Você também pode usar esse arquivo para criar novas variáveis de ambiente e montagens de volume.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Configuração adicional com KubernetesLocalProcessConfig. YAML

O `KubernetesLocalProcessConfig.yaml` arquivo permite replicar as variáveis de ambiente e os arquivos montados disponíveis para o pods em seu cluster. Para obter mais informações sobre as opções de configuração adicionais, consulte [Configurar processo local com kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Usando recursos de roteamento para o desenvolvimento em isolamento

Por padrão, o processo local com kubernetes redireciona todo o tráfego de um serviço para o seu computador de desenvolvimento. Você também tem a opção de usar os recursos de roteamento para redirecionar apenas as solicitações para um serviço proveniente de um subdomínio para seu computador de desenvolvimento. Esses recursos de roteamento permitem que você use o processo local com o kubernetes para desenvolver em isolamento e evitar a interrupção de outro tráfego no cluster.

A animação a seguir mostra dois desenvolvedores que trabalham no mesmo cluster isoladamente:

![Isolamento animado de ilustração de GIF](media/local-process-kubernetes/lpk-graphic-isolated.gif)

Quando você habilita o trabalho em isolamento, o processo local com kubernetes faz o seguinte, além de se conectar ao seu cluster kubernetes:

* Verifica se o cluster kubernetes não tem Azure Dev Spaces habilitado.
* Replica o serviço escolhido no cluster no mesmo namespace e adiciona um rótulo *Routing.VisualStudio.Io/Route-from=service_name* e *Routing.VisualStudio.Io/Route-on-header=kubernetes-Route-as: GENERATED_NAME* anotação.
* Configura e inicia o Gerenciador de roteamento no mesmo namespace no cluster kubernetes. O Gerenciador de roteamento usa um seletor de rótulo para procurar o rótulo *Routing.VisualStudio.Io/Route-from=service_name* e *Routing.VisualStudio.Io/Route-on-header=kubernetes-Route-as: GENERATED_NAME* anotação ao configurar o roteamento em seu namespace.

Se o processo local com kubernetes detectar que Azure Dev Spaces está habilitado no cluster do kubernetes, será solicitado que você desabilite Azure Dev Spaces antes de poder usar o processo local com o kubernetes.

O Gerenciador de roteamento faz o seguinte quando é iniciado:
* Duplica todas as insere encontradas no namespace usando o *GENERATED_NAME* para o subdomínio. 
* Cria um pod Envoy para cada serviço associado ao insere duplicado com o subdomínio *GENERATED_NAME* .
* Cria um pod Envoy adicional para o serviço no qual você está trabalhando isoladamente. Isso permite que as solicitações com o subdomínio sejam roteadas para o computador de desenvolvimento.
* Configura as regras de roteamento para cada pod Envoy para manipular o roteamento de serviços com o subdomínio.

Quando uma solicitação com o subdomínio *GENERATED_NAME* é recebida no cluster, um cabeçalho *kubernetes-Route-as = GENERATED_NAME* é adicionado ao à solicitação. O Envoy pods manipula o roteamento dessa solicitação para o serviço apropriado no cluster. Se a solicitação for roteada para o serviço que está sendo trabalhado no isolamento, essa solicitação será redirecionada para o computador de desenvolvimento pelo agente remoto.

Quando uma solicitação sem o subdomínio *GENERATED_NAME* é recebida no cluster, nenhum cabeçalho é adicionado à solicitação. O Envoy pods manipula o roteamento dessa solicitação para o serviço apropriado no cluster. Se a solicitação for roteada para o serviço que está sendo substituído, essa solicitação será roteada para o serviço original em vez do agente remoto.

> [!IMPORTANT]
> Cada serviço no cluster deve encaminhar o cabeçalho *kubernetes-Route-as = GENERATED_NAME* ao fazer solicitações adicionais. Por exemplo, quando o *servicea* recebe uma solicitação, ele faz uma solicitação para *serviceB* antes de retornar uma resposta. Neste exemplo, o *servicea* precisa encaminhar o cabeçalho *kubernetes-Route-as = GENERATED_NAME* em sua solicitação para *serviceB*. Algumas linguagens, como [ASP.net][asp-net-header], podem ter métodos para manipular a propagação do cabeçalho.

Quando você se desconecta do cluster, por padrão, o processo local com kubernetes removerá todos os pods de envoy e o serviço duplicado. 

> ANOTAÇÕES A implantação e o serviço do Gerenciador de roteamento permanecerão em execução no seu namespace. Para remover a implantação e o serviço, execute os comandos a seguir para seu namespace.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnóstico e registro em log

Ao usar o processo local com o kubernetes para se conectar ao cluster, os logs de diagnóstico do cluster são registrados no [diretório temporário][azds-tmp-dir]do computador de desenvolvimento.

## <a name="limitations"></a>Limitações

O processo local com kubernetes tem as seguintes limitações:

* O processo local com o kubernetes redireciona o tráfego de um único serviço para seu computador de desenvolvimento. Você não pode usar o processo local com kubernetes para redirecionar vários serviços ao mesmo tempo.
* Um serviço deve ser apoiado por um único pod para se conectar a esse serviço. Você não pode se conectar a um serviço com vários pods, como um serviço com réplicas.
* Um pod pode ter apenas um único contêiner em execução nesse pod para o processo local com kubernetes para se conectar com êxito. O processo local com kubernetes não pode se conectar a serviços com pods que têm contêineres adicionais, como contêineres sidecar injetados por malhas de serviços.
* O processo local com kubernetes precisa de permissões elevadas para executar em seu computador de desenvolvimento para editar o arquivo de hosts.
* O processo local com kubernetes não pode ser usado em clusters com Azure Dev Spaces habilitado.

### <a name="local-process-with-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Processo local com kubernetes e clusters com Azure Dev Spaces habilitado

Você não pode usar o processo local com o kubernetes em um cluster com Azure Dev Spaces habilitado. Se você quiser usar o processo local com kubernetes em um cluster com Azure Dev Spaces habilitado, será necessário desabilitar o Azure Dev Spaces antes de se conectar ao cluster.

## <a name="next-steps"></a>Próximas etapas

Para começar a usar o processo local com o kubernetes para se conectar ao seu computador de desenvolvimento local ao cluster, consulte [usar processo local com kubernetes](local-process-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-local-process-with-kubernetes.md