---
title: Depuração remota do .NET Core no Linux | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23bc0fa990a79b1855ec382f42248a0f847c3c9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78200919"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Depuração remota do .NET Core no Linux usando SSH

A partir do Visual Studio 2017, você pode anexar a processos do .NET Core em execução no Linux por SSH. Este artigo descreve como configurar a depuração e como depurar.

## <a name="prerequisites"></a>Pré-requisitos

No computador do Visual Studio, você precisa instalar a carga de trabalho de **desenvolvimento de ASP.net e Web** ou a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** .

No servidor Linux, você precisa instalar o servidor SSH, descompactar e instalar o com a rotação ou wget. Por exemplo, no Ubuntu, você pode fazer isso executando:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Compilar e implantar o aplicativo

Para preparar seu aplicativo para depuração:

- Considere o uso de uma configuração de depuração ao compilar o aplicativo. É muito mais difícil depurar o código compilado de varejo (uma configuração de versão) do que o código compilado por depuração. Se você precisar usar uma configuração de versão, primeiro desabilite Apenas Meu Código. Para desabilitar essa configuração, escolha **ferramentas**  >  **Opções**  >  **depuração**e, em seguida, desmarque **habilitar apenas meu código**.

- Verifique se o projeto está configurado para produzir [PDBs portáteis](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (que é a configuração padrão) e verifique se os PBDs estão no mesmo local que o dll. Para configurar isso no Visual Studio, clique com o botão direito do mouse no projeto e escolha **Propriedades**  >  **criar**  >  informações**avançadas**de  >  **depuração**.

Você pode usar vários métodos para implantar o aplicativo antes da depuração. Por exemplo, você pode:

- Copie as fontes para o computador de destino e crie com ```dotnet build``` o no computador Linux.

- Crie o aplicativo no Windows e transfira os artefatos de compilação para o computador Linux. (Os artefatos de compilação consistem no próprio aplicativo, em todas as bibliotecas de tempo de execução das quais ele pode depender e na *.deps.jsno* arquivo.)

## <a name="attach-the-debugger"></a>Anexar o depurador

Depois que os computadores estiverem configurados, inicie o aplicativo no computador Linux e, em seguida, você estará pronto para anexar o depurador.

1. No Visual Studio, escolha **depurar**  >  **anexar ao processo...**.

1. Na lista **tipo de conexão** , selecione **SSH**.

1. Altere o **destino de conexão** para o endereço IP ou nome de host do computador de destino.

1. Localize o processo que você deseja depurar.

   Seu código é executado em um nome de processo exclusivo ou um processo chamado dotnet. Para localizar o processo no qual você está interessado, verifique a coluna **título** , que mostra os argumentos de linha de comando para o processo.

   No exemplo a seguir, você verá uma lista de processos de um computador Linux remoto em um transporte SSH exibido na caixa de diálogo **anexar ao processo** .

   ![Anexar ao processo do Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Escolha **anexar**.

1. Na caixa de diálogo que aparece, selecione o tipo de código que você deseja depurar. Escolha **gerenciado (.NET Core para UNIX)**.

1. Use os recursos de depuração do Visual Studio para depurar o aplicativo.

   No exemplo a seguir, você vê o depurador do Visual Studio interrompido em um ponto de interrupção no código em execução em um computador Linux remoto.

   ![Atingir um ponto de interrupção](media/remote-debug-linux-over-ssh-hit-breakpoint.png)