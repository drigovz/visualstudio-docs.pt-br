---
title: Solução de problemas de erros de cliente do Docker no Windows | Microsoft Docs
description: Solucione os problemas encontrados na utilização do Visual Studio para criar e implantar aplicativos Web no Docker ou no Windows usando o Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: d8aa3028a12bcfb49f2663b2bea688baf14fd7f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027275"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Solucionar problemas de desenvolvimento do Visual Studio com o Docker

Quando você está trabalhando com o Visual Studio Container Tools, você pode encontrar problemas durante a construção ou depuração do seu aplicativo. A seguir estão algumas etapas comuns para solução de problemas.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Compartilhamento de volume não está habilitado. Habilite o compartilhamento de volume nas configurações do Docker CE para Windows (somente contêineres do Linux)

Para resolver o problema:

1. Clique com o botão direito do mouse em **Docker para Windows** na área de notificação e selecione **Configurações**.
1. Selecione **Unidades Compartilhadas** e compartilhe a unidade do sistema junto com a unidade na qual o projeto reside.

> [!NOTE]
> Se o arquivos aparecer compartilhado, você ainda precisará clicar no link "Redefinir credenciais…" na parte inferior da caixa de diálogo para reabilitar o volume de compartilhamento. Para continuar depois de redefinir as credenciais, talvez seja necessário reiniciar o Visual Studio.

![unidades compartilhadas](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Versões do Visual Studio mais tarde do visual studio 2017 versão 15.6 prompt quando **unidades compartilhadas** não estão configuradas.

### <a name="container-type"></a>Tipo de contêiner

Ao adicionar o suporte ao Docker a um projeto, escolha um contêiner do Windows ou do Linux. O host do Docker deve estar executando o mesmo tipo de contêiner. Para alterar o tipo de contêiner na instância do Docker em execução, clique com o botão direito do mouse no ícone do Docker na Bandeja do Sistema e escolha **Alternar para contêineres do Windows...** ou **Alternar para contêineres do Linux...**.

## <a name="unable-to-start-debugging"></a>Não é possível iniciar a depuração

Uma razão para isso pode estar relacionada a ter componentes de depuração obsoletos na pasta de perfil do usuário. Execute os seguintes comandos para remover essas pastas para que os componentes de depuração mais recentes sejam baixados na próxima sessão de depuração.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Erros específicos de rede ao depurar o aplicativo

Tente executar o script baixado de [Rede de Host do Contêiner de Limpeza](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), que atualizará os componentes relacionados à rede no seu computador host.

## <a name="mounts-denied"></a>Montagens negadas

Ao usar o Docker para macOS, talvez você encontre um erro que referencie a pasta /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Adicione a pasta à guia Compartilhamento de Arquivos no Docker

## <a name="docker-users-group"></a>Grupo de usuários docker

Você pode encontrar o seguinte erro no Visual Studio ao trabalhar com contêineres:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Você deve ser um membro do grupo 'docker-users' para ter permissões para trabalhar com contêineres Docker.  Para adicionar-se ao grupo no Windows 10, siga estas etapas:

1. A partir do menu Iniciar, abra **o Gerenciamento de Computadores**.
1. Expanda **usuários e grupos locais**e escolha **Grupos**.
1. Encontre o grupo **docker-users,** clique com o botão direito do mouse e escolha **Adicionar ao grupo**.
1. Adicione sua conta de usuário ou contas.
1. Assine e faça login novamente para que essas mudanças surtam efeito.

Você também pode `net localgroup` usar o comando no prompt de comando Administrador para adicionar usuários a grupos específicos.

```cmd
net localgroup docker-users DOMAIN\username /add
```

No PowerShell, use a função [Add-LocalGroupMember.](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)

## <a name="low-disk-space"></a>Pouco espaço em disco

Por padrão, o Docker armazena imagens na pasta *%ProgramData%/Docker/,* que normalmente está\*na unidade do sistema, *C:\ProgramData\Docker . Para evitar que as imagens ocupem espaço valioso na unidade do sistema, você pode alterar a localização da pasta de imagem.  A partir do ícone Docker na barra de tarefas, abra as configurações do Docker, escolha **Daemon**e mude de **Básico** para **Avançado**. No painel de edição, `graph` adicione a configuração da propriedade com o valor da localização desejada para imagens do Docker:

```json
    "graph": "D:\\mypath\\images"
```

![Captura de tela da configuração de localização da imagem do Docker](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Clique **em Aplicar** para reiniciar o Docker. Essas etapas modificam o arquivo de configuração em *%ProgramData%\docker\config\daemon.json*. As imagens construídas anteriormente não são movidas.

## <a name="microsoftdockertools-github-repo"></a>Repositório Microsoft/DockerTools GitHub

Para quaisquer outros problemas que encontrar, consulte problemas do [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).