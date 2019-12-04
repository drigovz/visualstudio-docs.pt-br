---
title: Modificar o Visual Studio
titleSuffix: ''
description: Saiba como modificar o Visual Studio, passo a passo.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 12/03/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23e44479bedfdb44b2375baae9f342f47b38700b
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810067"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modificar o Visual Studio adicionando ou removendo cargas de trabalho e componentes

::: moniker range="vs-2019"

É fácil modificar o Visual Studio para que ele inclua apenas o que você deseja, quando você deseja. Para fazer isso, abra o Instalador do Visual Studio para adicionar ou remover componentes e cargas de trabalho.

::: moniker-end

::: moniker range="vs-2017"

Não apenas tornamos mais fácil para você personalizar o Visual Studio para corresponder às etapas que deseja realizar, mas também facilitamos a customização do Visual Studio. Para fazer isso, inicie o novo instalador do Visual Studio e faça as alterações desejadas.

::: moniker-end

Veja como.

>[!IMPORTANT]
>Para instalar, atualizar ou modificar o Visual Studio, faça logon com uma conta que tenha permissões administrativas. Para saber mais, confira [Permissões de usuário e Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>Modificar cargas de trabalho

::: moniker range="vs-2017"

 As [cargas de trabalho](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) contêm os recursos necessários para a linguagem de programação ou a plataforma que está sendo usada. Use cargas de trabalho para modificar o Visual Studio para que ele dê suporte ao trabalho que você deseja fazer, quando desejar fazê-lo.

::: moniker-end

::: moniker range="vs-2019"

 As cargas de trabalho contêm os recursos necessários para a linguagem de programação ou plataforma que você está usando. Use cargas de trabalho para modificar o Visual Studio para que ele dê suporte ao trabalho que você deseja fazer, quando desejar fazê-lo.

::: moniker-end

>[!NOTE]
> O procedimento a seguir pressupõe que você tenha uma conexão de internet.
>
> Para obter mais informações sobre como modificar uma [instalação offline](create-an-offline-installation-of-visual-studio.md) do Visual Studio criada anteriormente, confira as páginas [Atualizar uma instalação baseada em rede do Visual Studio](update-a-network-installation-of-visual-studio.md) e [Controlar as atualizações em implantações baseadas em rede do Visual Studio](controlling-updates-to-visual-studio-deployments.md).

::: moniker range="vs-2017"

1. Localize o Instalador do Visual Studio no computador.

     Por exemplo, em um computador que executa o Windows 10, selecione **Iniciar** e, em seguida, role até a letra **I**, onde ele está listado como **Instalador do Visual Studio**.

     ![Instalador do Visual Studio](media/locate-the-visual-studio-installer.png "Localize o instalador do Microsoft Visual Studio")

     >[!TIP]
     >Em alguns computadores, o Instalador do Visual Studio poderá estar listado sob a letra **“M”** como **Instalador do Microsoft Visual Studio**.<br/><br/> Como alternativa, encontre o Instalador do Visual Studio no seguinte local: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Clique ou toque para iniciar o instalador e, em seguida, escolha **Modificar**.

     ![Iniciar ou modificar o Visual Studio](media/modify-visual-studio.png "Modificar o Visual Studio 2017")

     Se houver uma atualização pendente, o botão Modificar estará em um local diferente. Dessa forma, você pode modificar o Visual Studio sem atualizá-lo, caso queria. Clique em **Mais** e, em seguida, escolha **Modificar**.

     ![Atualizar ou modificar o Visual Studio](media/modify-or-update-visual-studio.png "Atualizar ou modificar o Visual Studio 2017")

1. Na tela **Cargas de Trabalho**, marque ou desmarque as cargas de trabalho que você deseja instalar ou desinstalar.

    ![Caixa de diálogo de instalação do Visual Studio 2017](media/modify-workloads.png "Escolha uma carga de trabalho no Visual Studio 2017")

1. Escolha **Modificar** novamente.

1. Depois da instalação d novas cargas de trabalho e componentes, escolha **Iniciar**.

::: moniker-end

::: moniker range="vs-2019"

1. Localize o Instalador do Visual Studio no computador.

     Por exemplo, em um computador que executa o Windows 10, selecione **Iniciar** e, em seguida, role até a letra **I**, onde ele está listado como **Instalador do Visual Studio**.

     ![Abrir o Instalador do Visual Studio do Windows](media/vs-2019/vs-installer-windows-start.png "Abra o Instalador do Visual Studio")

     > [!NOTE]
     > Também é possível encontrar o Instalador do Visual Studio no seguinte local:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Talvez você precise atualizar o instalador antes de continuar. Nesse caso, siga os prompts.

1. No instalador, procure a edição do Visual Studio instalada por você e escolha **Modificar**.

     ![Atualizar ou modificar o Visual Studio](media/vs-2019/vs-installer-modify.png "Atualizar ou modificar o Visual Studio 2019")

1. Na guia **Cargas de Trabalho**, selecione ou anule a seleção das cargas de trabalho que você deseja instalar ou desinstalar.

    ![Caixa de diálogo de instalação do Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Escolha uma carga de trabalho no Visual Studio 2019")

1. Escolha se deseja aceitar a opção padrão **Instalar durante o download** ou a opção **Baixar tudo, depois instalar**.

    ![Opções de instalação do Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Escolha instalar durante o download ou para baixar primeiro e instalar mais tarde")

    A opção "Baixar tudo, depois instalar" é útil se você deseja baixar primeiro e instalar mais tarde.

1. Escolha **Modificar**.

1. Depois da instalação de novas cargas de trabalho e componentes, escolha **Iniciar** do Instalador do Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Modificar componentes individuais

Se você não quiser instalar cargas de trabalho nem personalizar sua instalação do Visual Studio, escolha a guia **Componentes Individuais** do Instalador do Visual Studio, selecione o que deseja e siga os prompts.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Lista de IDs de componente e carga de trabalho do Visual Studio](workload-and-component-ids.md)
* [Atualizar o Visual Studio](update-visual-studio.md)
* [Atualizar uma instalação em rede do Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Atualizar o Visual Studio enquanto estiver em uma linha de base de manutenção](update-servicing-baseline.md)
* [Atualizações de controle para implantações do Visual Studio com base em rede](controlling-updates-to-visual-studio-deployments.md)
* [Desinstalar o Visual Studio](uninstall-visual-studio.md)
