---
title: Implantar na pasta local
description: Implantar um aplicativo em uma pasta local
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67256273"
---
1. No **Gerenciador de soluções**, clique com botão direito no nó do projeto e selecione **Publish** (para formulários da Web, **Publicar Web App**).

    Se você já tiver configurado anteriormente quaisquer perfis de publicação, o painel **Publicar** será exibido. Clique em **novo perfil**.

1. No **Publish** caixa de diálogo, selecione **pasta**, clique em **procurar**e crie uma nova pasta, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Para um aplicativo de formulários da Web, escolha **personalizado** na caixa de diálogo Publicar, insira um nome de perfil e escolha **Okey**.

1. Clique em **criar perfil** na lista suspensa (**publicar** é o valor padrão).

1. No **Publish** caixa de diálogo, clique no **configurações** vincular e, em seguida, selecione o **configurações** guia.

1. Definir a configuração para **Debug**, selecione **excluir todos os arquivos existentes antes de publicar**e, em seguida, clique em **salvar**.

    > [!NOTE]
    > Se você usar uma compilação de versão, você desabilitar depuração no arquivo Web. config quando você publica.

1. Clique em **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    O aplicativo publica uma **depurar** configuração do projeto para a pasta local. Mostra progresso na janela de saída.

1. Copiar o diretório de projeto do ASP.NET do computador do Visual Studio para o diretório local configurado para o aplicativo ASP.NET (neste exemplo, **C:\Publish**) no computador do Windows Server. Neste tutorial, vamos supor que você está copiando manualmente, mas você pode usar outras ferramentas como PowerShell, Xcopy ou Robocopy.

    > [!CAUTION]
    > Se você precisar fazer alterações no código ou recompilação, você deve republicar e repita esta etapa. O executável que você copiou para o computador remoto deve corresponder exatamente, seu local de origem e símbolos.    Se você não fizer isso, você receberá um `cannot find or open the PDB file` aviso no Visual Studio quando você tenta depurar o processo.

1. No Windows Server, verifique se que você pode executar o aplicativo corretamente abrindo o aplicativo em seu navegador.

    Se o aplicativo não funcionar corretamente, pode haver uma incompatibilidade entre a versão do ASP.NET instalado no seu servidor e em seu computador do Visual Studio, ou você pode ter um problema com a configuração do IIS ou no site da Web. Verifique novamente as etapas anteriores.
