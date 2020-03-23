---
title: Registros de contêineres docker, variáveis de ambiente e acesso ao sistema de arquivos
description: Descreve como melhorar sua capacidade de depurar e diagnosticar seus aplicativos baseados em contêineres no Visual Studio usando uma janela de ferramenta para ver o que está acontecendo dentro dos contêineres que hospedam seu aplicativo.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b4670c003c06f8d16979589a4dce5abf33d5e27d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027301"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Como ver e diagnosticar contêineres e imagens no Visual Studio

Você pode ver o que está acontecendo dentro dos contêineres que hospedam seu aplicativo usando a janela **Containers.** Se você está acostumado a usar o prompt de comando para executar comandos Docker para visualizar e diagnosticar o que está acontecendo com seus contêineres, esta janela fornece uma maneira mais conveniente de monitorar seus contêineres sem sair do Visual Studio IDE.

## <a name="prerequisites"></a>Pré-requisitos

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 versão 16.4 Preview 2](https://visualstudio.microsoft.com/downloads) ou posterior, ou se você estiver usando uma versão anterior do Visual Studio 2019, instale a extensão de [janela Containers](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Exibir informações sobre seus contêineres

A janela **Containers** é aberta automaticamente quando você inicia um projeto .NET contêiner. Para ver seus contêineres no Visual Studio a qualquer momento, use **Ctrl**+**Q** para ativar a caixa visual studio search e digite `Containers` e escolha o primeiro item. Você também pode abrir a janela **Containers** a partir do menu principal. Use o caminho do menu **Exibir** > **Outros** > **contêineres do Windows**.  

![Captura de tela da guia Ambiente na janela Containers](media/view-and-diagnose-containers/container-window.png)

No lado esquerdo, você vê a lista de recipientes em sua máquina local. Os recipientes associados à sua solução são mostrados em **Recipientes de Solução**. À direita, você vê um painel com guias para **Meio Ambiente,** **Portas,** **Logs**e **Arquivos**.

> [!TIP]
> Você pode facilmente personalizar onde a janela da ferramenta **Containers** está encaixada no Visual Studio. Consulte [Personalização de layouts de janelas no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Por padrão, a janela **Containers** é encaixada com a janela **Relógio** quando o depurador estiver sendo executado.

## <a name="view-environment-variables"></a>Ver variáveis de ambiente

A guia **Ambiente** mostra as variáveis de ambiente no recipiente. Para o contêiner do seu aplicativo, você pode definir essas variáveis de muitas maneiras, por exemplo, no Arquivo Docker, em um arquivo .env, ou usando a opção -e quando você inicia um contêiner usando um comando Docker.

![Captura de tela da guia Ambiente na janela Containers](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Quaisquer alterações nas variáveis do ambiente não são refletidas em tempo real. Além disso, as variáveis de ambiente nesta guia são as variáveis do ambiente do sistema no contêiner, e não refletem variáveis de ambiente do usuário locais para o aplicativo.

## <a name="view-port-mappings"></a>Exibir mapeamentos de portas

Na guia **Portas,** você pode verificar os mapeamentos de portas que estão em vigor para o seu contêiner.

![Tela de captura de tela da guia Portas na janela Containers](media/view-and-diagnose-containers/containers-ports.png)

Portas bem conhecidas estão vinculadas, portanto, se houver conteúdo disponível em uma porta, você pode clicar no link para abrir o navegador.

## <a name="view-logs"></a>Exibir logs

A guia **Logs** mostra `docker logs` os resultados do comando. Por padrão, a guia mostra fluxos stdout e stderr em um contêiner, mas você pode configurar a saída. Para obter detalhes, consulte [o registro de Docker](https://docs.docker.com/config/containers/logging/).  Por padrão, a guia **Logs** transmite os logs, mas você pode desativar isso escolhendo o botão **Parar** na guia.

![Captura de tela da guia Logs na janela Containers](media/view-and-diagnose-containers/containers-logs.png)

Para limpar os registros, use o botão **Limpar** na guia **Logs.**  Para obter todos os registros, use o botão **Atualizar.**

> [!NOTE]
> O Visual Studio redireciona automaticamente stdout e stderr para a janela **De saída** quando você é executado sem depuração com contêineres do Windows, de modo que os contêineres do Windows iniciados a partir do Visual Studio usando **Ctrl**+**F5** não exibirão logs nesta guia; em vez disso, use a janela **Saída.**

## <a name="view-the-filesystem"></a>Exibir o sistema de arquivos

Na guia **Arquivos,** você pode visualizar o sistema de arquivos do contêiner, incluindo a pasta do aplicativo que contém o seu projeto.

![Tela de captura de tela de arquivos na janela Containers](media/view-and-diagnose-containers/container-filesystem.png)

Para abrir arquivos no Visual Studio, navegue até o arquivo e clique duas vezes nele, ou clique com o botão direito do mouse e escolha **Abrir**. O Visual Studio abre arquivos no modo somente leitura.

![Captura de tela do arquivo aberto para visualização no Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Usando a guia **Arquivos,** você pode visualizar registros de aplicativos, como logs de IIS, arquivos de configuração e outros arquivos de conteúdo no sistema de arquivos do contêiner.

## <a name="start-stop-and-remove-containers"></a>Inicie, pare e remova os recipientes

Por padrão, a janela **Containers** mostra todos os recipientes na máquina que o Docker gerencia. Você pode usar os botões da barra de ferramentas para iniciar, parar ou remover (excluir) um recipiente que você não deseja mais.  Esta lista é atualizada dinamicamente à medida que os contêineres são criados ou removidos.

## <a name="open-a-terminal-window-in-a-running-container"></a>Abra uma janela de terminal em um contêiner em execução

Você pode abrir uma janela de terminal (prompt de comando ou shell interativo) no contêiner usando o botão **Janela de Terminal Aberto** na janela **container.**

![Captura de tela da janela do terminal aberto na janela containers](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Para contêineres do Windows, o prompt de comando do Windows é aberto. Para contêineres Linux, ele abre uma janela usando a concha bash.

![Captura de tela da janela do bash](media/view-and-diagnose-containers/container-bash-window.png)

Normalmente, a janela do terminal se abre fora do Visual Studio como uma janela separada. Se você quiser um ambiente de linha de comando integrado ao Visual Studio IDE como uma janela de ferramenta ancorável, você pode instalar [o Whack Whack Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Anexar o depurador a um processo

Você pode anexar o depurador a um processo que está sendo executado no contêiner usando o botão **Anexar ao processo** na barra de ferramentas da janela Containers. Quando você usa este botão, a caixa de diálogo **Anexar ao processo** é exibida e mostra os processos disponíveis que estão sendo executados no contêiner.  

![Captura de tela da caixa de diálogo Anexar ao processo](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Você pode anexar a processos gerenciados no contêiner. Para procurar um processo em outro contêiner, use o botão **Encontrar** e selecione outro contêiner na caixa de diálogo **Selecionar contêiner Docker.**

## <a name="viewing-images"></a>Visualização de imagens

Você também pode visualizar imagens na máquina local usando a guia **Imagens** na janela **Containers.** Imagens retiradas de repositórios externos são agrupadas em uma vista de árvore. Selecione uma imagem para inspecionar os detalhes da imagem.

Para remover uma imagem, clique com o botão direito do mouse na imagem na visão da árvore e escolha **Remover**ou selecionar a imagem e use o botão **Remover** na barra de ferramentas.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre as Ferramentas de Contêineres disponíveis no Visual Studio lendo a visão geral das [ferramentas de contêiner.](overview.md)

## <a name="see-also"></a>Confira também

[Desenvolvimento de Contêineres em Estúdio Visual](/visualstudio/containers)

[Marketplace de Extensões para Visual Studio](https://marketplace.visualstudio.com/)
