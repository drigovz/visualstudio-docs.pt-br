---
title: Reparar o Visual Studio
titleSuffix: ''
description: Saiba como reparar uma instalação do Visual Studio 2017
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 368ca6619a2fcff48cc3bcc7eb70913247b631b2
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114740"
---
# <a name="repair-visual-studio"></a>Reparar o Visual Studio

::: moniker range="vs-2017"

Às vezes, a instalação do Visual Studio é danificada ou corrompida. Um reparo pode corrigir isso.

1. Localize o **Instalador do Visual Studio** no computador.

     Por exemplo, em um computador que executa a Atualização de Aniversário do Windows 10 ou posterior, selecione **Iniciar** e, em seguida, role até a letra **V**, onde ele estará listado como **Instalador do Visual Studio**.

   > [!NOTE]
   > Em alguns computadores, o Instalador do Visual Studio poderá estar listado sob a letra **“M”** como **Instalador do Microsoft Visual Studio**.
   >
   > Como alternativa, encontre o Instalador do Visual Studio no seguinte local: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Abra o instalador, escolha **Mais** e, em seguida, escolha **Reparar**.

    ![Reparar o Visual Studio do Instalador do Visual Studio](media/repair-visual-studio.png "Reparar o Visual Studio do Instalador do Visual Studio")

   > [!NOTE]
   > Reparar o Visual Studio redefinirá o ambiente. As personalizações locais, como as extensões do usuário instaladas sem elevação, as configurações de usuário e os perfis serão removidos. As configurações sincronizadas, como temas, cores, associações de teclas serão restauradas.
   >

   > [!TIP]
   > A opção **Reparar** aparecerá apenas em instâncias instaladas do Visual Studio. Se você não vir a opção **Reparar**, pode ser que tenha selecionado **Mais** em uma versão que estava listada no Instalador do Visual Studio como "Disponível" em vez de "Instalada".

::: moniker-end

::: moniker range="vs-2019"

1. Localize o Instalador do Visual Studio no computador.

     Por exemplo, em um computador que executa o Windows 10, selecione **Iniciar** e, em seguida, role até a letra **I**, onde ele está listado como **Instalador do Visual Studio**.

     ![Abra o Instalador do Visual Studio](media/vs-2019/vs-installer-windows-start.png "Abra o Instalador do Visual Studio")

     > [!NOTE]
     > Também é possível encontrar o Instalador do Visual Studio no seguinte local:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Talvez você precise atualizar o instalador antes de continuar. Nesse caso, siga os prompts.

1. No instalador, procure a edição do Visual Studio instalada por você. Em seguida, escolha **Mais** e escolha **Reparar**.

     ![Reparar o Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Reparar o Visual Studio 2019")

   > [!NOTE]
   > Reparar o Visual Studio redefinirá o ambiente. As personalizações locais, como as extensões do usuário instaladas sem elevação, as configurações de usuário e os perfis serão removidos. As configurações sincronizadas, como temas, cores, associações de teclas serão restauradas.
   >

   > [!TIP]
   > A opção **Reparar** aparecerá apenas em instâncias instaladas do Visual Studio. Se você não vir a opção **Reparar**, pode ser que tenha selecionado **Mais** em uma versão que estava listada no Instalador do Visual Studio como "Disponível" em vez de "Instalada".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Veja também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Atualizar o Visual Studio](update-visual-studio.md)
* [Desinstalar o Visual Studio](uninstall-visual-studio.md)
* [Solução de problemas de instalação e atualização do Visual Studio](troubleshooting-installation-issues.md)
