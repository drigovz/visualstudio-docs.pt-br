---
title: Anexar a um processo em execução em um contêiner do Docker
description: Saiba como depurar um aplicativo que executa um contêiner do Docker usando o Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: f6e2b851057d924353e6e1e9a211fcbb294353c8
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761258"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Anexar a um processo em execução em um contêiner do Docker 

Você pode depurar aplicativos em execução em um contêiner do Windows Docker ou em um contêiner do Docker do Linux .NET Core usando o Visual Studio.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Anexar a um processo em execução em um contêiner do Docker do Linux

Você pode anexar o depurador do Visual Studio a um processo em execução em um contêiner do Docker do Linux .NET Core em seu computador local ou remoto usando a caixa de diálogo **anexar ao processo** .

> [!IMPORTANT]
> Para usar esse recurso, você deve instalar a carga de trabalho de desenvolvimento entre plataformas do .NET Core e ter acesso local ao código-fonte.

**Para anexar a um processo em execução em um contêiner do Docker do Linux:**

1. No Visual Studio, selecione **depurar > anexar ao processo (CTRL + ALT + P)** para abrir a caixa de diálogo **anexar ao processo** .

![Captura de tela da caixa de diálogo anexar ao processo no Visual Studio mostrando um tipo de conexão do Docker (contêiner do Linux).](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Defina o **tipo de conexão** como **Docker (contêiner do Linux)**.
3. Selecione **Localizar...** para definir o **destino de conexão** por meio da caixa de diálogo **selecionar contêiner do Docker** .

    Você pode depurar um processo de contêiner do Docker localmente ou remotamente.

    **Para depurar um processo de contêiner do Docker localmente:**
    1. Definir **host da CLI do Docker** para o **computador local**.
    1. Selecione um contêiner em execução para anexar na lista e clique em **OK**.

    ![Selecionar menu do contêiner do Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Para depurar um processo de contêiner do Docker remotamente:**

    > [!NOTE]
    > Há duas opções para se conectar remotamente a um processo em execução em um contêiner do Docker. A primeira opção, para usar SSH, é ideal se você não tiver as ferramentas do Docker instaladas em seu computador local.  Se você tiver as ferramentas do Docker instaladas localmente e tiver um daemon do Docker configurado para aceitar solicitações remotas, tente a segunda opção, usando um daemon do Docker.

    1. **_Para se conectar a um computador remoto via SSH:_* _
        1. Selecione _ *Adicionar..* . * para se conectar a um sistema remoto.<br/>
        ![Conectar-se a um sistema remoto](../debugger/media/connect-remote-system.png "Conectar-se a um sistema remoto")
        1. Selecione um contêiner em execução ao qual anexar depois de se conectar ao SSH ou ao daemon com êxito e pressione **OK**.

    1. **_Para definir o destino para um contêiner remoto executando um processo por meio de um [daemon do Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
        1. Especifique o endereço do daemon (ou seja, via TCP, IP, etc.) em _ *host do Docker (opcional)** e clique no link atualizar.
        1. Selecione um contêiner em execução ao qual anexar depois de se conectar ao daemon com êxito e pressione **OK**.

4. Escolha o processo de contêiner correspondente na lista de **processos disponíveis** e selecione **anexar** para iniciar a depuração do processo de contêiner do C# no Visual Studio!

    ![Captura de tela da caixa de diálogo anexar ao processo no Visual Studio. O tipo de conexão é definido como Docker (contêiner do Linux) e o processo dotnet é selecionado.](../debugger/media/docker-attach-complete.png "Menu de anexação do Docker do Linux concluído")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Anexar a um processo em execução em um contêiner do Docker do Windows

Você pode anexar o depurador do Visual Studio a um processo em execução em um contêiner do Docker do Windows em seu computador local usando a caixa de diálogo **anexar ao processo** .

> [!IMPORTANT]
> Para usar esse recurso com um processo do .NET Core, você deve instalar a carga de trabalho de desenvolvimento entre plataformas do .NET Core e ter acesso local ao código-fonte.

**Para anexar a um processo em execução em um contêiner do Docker do Windows:**

1. No Visual Studio, selecione **depurar > anexar ao processo** (ou **Ctrl + Alt + P**) para abrir a caixa de diálogo **anexar ao processo** .

   ![Captura de tela da caixa de diálogo anexar ao processo no Visual Studio mostrando um tipo de conexão do Docker (contêiner do Windows).](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Defina o **tipo de conexão** como **Docker (contêiner do Windows)**.
3. Selecione **Localizar...** para definir o **destino de conexão** usando a caixa de diálogo **selecionar contêiner do Docker** .

    > [!IMPORTANT]
    > O processo de destino deve ter a mesma arquitetura de processador que o contêiner do Windows do Docker em que está sendo executado.

   A definição do destino para um contêiner remoto via SSH não está disponível no momento e só pode ser feita usando um daemon do Docker.

    **_Para definir o destino para um contêiner remoto executando um processo por meio de um [daemon do Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
    1. Especifique o endereço do daemon (ou seja, via TCP, IP, etc.) em _ *host do Docker (opcional)** e clique no link atualizar.

    1. Selecione um contêiner em execução ao qual anexar depois de se conectar ao daemon com êxito e escolha OK.

4. Escolha o processo de contêiner correspondente na lista de **processos disponíveis** e selecione **anexar** para iniciar a depuração do processo de contêiner do C#.

    ![Captura de tela da caixa de diálogo anexar ao processo no Visual Studio. O tipo de conexão é definido como Docker (contêiner do Windows) e o processo de dotnet.exe está selecionado.](../debugger/media/docker-attach-complete-windows.png "Menu de anexação do Docker do Windows concluído")

5. Escolha o processo de contêiner correspondente na lista de processos disponíveis e escolha **anexar** para iniciar a depuração do processo de contêiner do C#.