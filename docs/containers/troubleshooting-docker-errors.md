---
title: Solução de problemas de erros de cliente do Docker no Windows | Microsoft Docs
description: Solucione os problemas encontrados na utilização do Visual Studio para criar e implantar aplicativos Web no Docker ou no Windows usando o Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 9535a7d88cb375d97867092eddf969095c327329
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729230"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Solucionar problemas de desenvolvimento do Visual Studio com o Docker

Quando você estiver trabalhando com as ferramentas de contêiner do Visual Studio, poderá encontrar problemas ao criar ou depurar seu aplicativo. A seguir estão algumas etapas comuns para solução de problemas.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Compartilhamento de volume não está habilitado. Habilite o compartilhamento de volume nas configurações do Docker CE para Windows (somente contêineres do Linux)

O compartilhamento de arquivos só precisa ser gerenciado se você estiver usando o Hyper-V com o Docker. Se você estiver usando o WSL 2, as etapas a seguir não serão necessárias e a opção de compartilhamento de arquivos não estará visível. Para resolver o problema:

1. Clique com o botão direito do mouse em **Docker para Windows** na área de notificação e selecione **Configurações**.
1. Selecione **recursos**  >  **compartilhamento de arquivos** e compartilhe a pasta que precisa ser acessada. O compartilhamento de toda a unidade do sistema é possível, mas não recomendado.

    ![unidades compartilhadas](media/troubleshooting-docker-errors/docker-settings-image.png)

> [!TIP]
> As versões do Visual Studio posteriores ao Visual Studio 2017 versão 15,6 serão solicitadas quando as **unidades compartilhadas** não estiverem configuradas.

## <a name="unable-to-start-debugging"></a>Não é possível iniciar a depuração

Uma razão para isso pode estar relacionada a ter componentes de depuração obsoletos na pasta de perfil do usuário. Execute os seguintes comandos para remover essas pastas para que os componentes de depuração mais recentes sejam baixados na próxima sessão de depuração.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Erros específicos de rede ao depurar o aplicativo

Tente executar o script baixado de [Rede de Host do Contêiner de Limpeza](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), que atualizará os componentes relacionados à rede no seu computador host.

## <a name="mounts-denied"></a>Montagens negadas

Ao usar o Docker para macOS, talvez você encontre um erro que referencie a pasta /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Adicione a pasta à guia Compartilhamento de arquivos no Docker.

## <a name="docker-users-group"></a>Grupo de usuários do Docker

Você pode encontrar o seguinte erro no Visual Studio ao trabalhar com contêineres:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Você deve ser membro do grupo ' Docker-users ' para ter permissões para trabalhar com contêineres do Docker.  Para se adicionar ao grupo no Windows 10, siga estas etapas:

1. No menu Iniciar, abra **Gerenciamento do computador**.
1. Expanda **usuários e grupos locais** e escolha **grupos**.
1. Localize o grupo **Docker-usuários** , clique com o botão direito do mouse e escolha **Adicionar ao grupo**.
1. Adicione sua conta de usuário ou contas.
1. Saia e entre novamente para que essas alterações entrem em vigor.

Você também pode usar o `net localgroup` comando no prompt de comando do administrador para adicionar usuários a grupos específicos.

```cmd
net localgroup docker-users DOMAIN\username /add
```

No PowerShell, use a função [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) .

## <a name="low-disk-space"></a>Pouco espaço em disco

Por padrão, o Docker armazena imagens na pasta *% ProgramData%/Docker/* , que normalmente está na unidade do sistema, * C:\ProgramData\Docker \* . Para evitar que as imagens gerem um espaço valioso na unidade do sistema, você pode alterar o local da pasta de imagens. Para fazer isso:

 1. Clique com o botão direito do mouse no ícone do Docker na barra de tarefas e selecione **configurações**.
 1. Selecione **mecanismo do Docker**. 
 1. No painel de edição, adicione a `graph` configuração de propriedade com o valor do local desejado para imagens do Docker:

```json
    "graph": "D:\\mypath\\images"
```

![Captura de tela do compartilhamento de arquivos do Docker](media/troubleshooting-docker-errors/docker-daemon-settings.png)

Clique em **aplicar & reiniciar**. Estas etapas modificam o arquivo de configuração em *% ProgramData% \docker\config\daemon.jsem*. As imagens criadas anteriormente não são movidas.

## <a name="container-type-mismatch"></a>Incompatibilidade de tipo de contêiner

Ao adicionar o suporte ao Docker a um projeto, escolha um contêiner do Windows ou do Linux. Se o host do servidor do Docker não estiver configurado para executar o mesmo tipo de contêiner que o destino do projeto, você provavelmente verá um erro semelhante ao mostrado abaixo:

![Captura de tela de incompatibilidade de host e projeto do Docker](media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png)

Para resolver o problema:

- Clique com o botão direito do mouse no ícone de Docker for Windows na bandeja do sistema e escolha **alternar para contêineres do Windows...** ou **alternar para contêineres do Linux...**.

## <a name="microsoftdockertools-github-repo"></a>Repositório Microsoft/DockerTools GitHub

Para quaisquer outros problemas que encontrar, consulte problemas do [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).

## <a name="see-also"></a>Consulte também

- [Solução de problemas do Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
