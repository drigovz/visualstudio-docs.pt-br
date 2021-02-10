---
title: Depuração do .NET Core no Linux
description: Depurar o .NET Core no Linux usando o Secure Shell (SSH) anexando a um processo. Prepare seu aplicativo para depuração. Crie e implante o aplicativo. Anexe o depurador.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99bfd1df6d977830e5b8e332efa3d0af653d3aec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934605"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Depurar o .NET Core no Linux usando o SSH anexando a um processo

A partir do Visual Studio 2017, você pode anexar a processos do .NET Core em execução em uma implantação do Linux local ou remota por SSH. Este artigo descreve como configurar a depuração e como depurar. Para cenários de depuração usando contêineres do Docker, consulte [anexar a um processo em execução em um contêiner do Docker](../debugger/attach-to-process-running-in-docker-container.md) e os artigos de [Ferramentas do contêiner](../containers/edit-and-refresh.md) em vez disso. Para depurar o Linux no WSL 2 do Visual Studio (sem anexar ao processo), consulte [depurar aplicativos .NET Core no WSL 2 com o Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md).

## <a name="prerequisites"></a>Pré-requisitos

- No computador do Visual Studio, você precisa instalar a carga de trabalho de **desenvolvimento de ASP.net e Web** ou a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** .

- No servidor Linux, você precisa instalar o servidor SSH, descompactar e instalar o com a rotação ou wget. Por exemplo, no Ubuntu, você pode fazer isso executando:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- No servidor Linux, [Instale o tempo de execução do .net no Linux](/dotnet/core/install/linux)e localize a página correspondente à sua distribuição do Linux (como Ubuntu). O SDK do .NET não é necessário.

- Para obter instruções de ASP.NET Core abrangentes, consulte [host ASP.NET Core no Linux com Nginx](/aspnet/core/host-and-deploy/linux-nginx) e [host ASP.NET Core no Linux com Apache](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Preparar seu aplicativo para depuração

Para preparar seu aplicativo para depuração:

- Considere o uso de uma configuração de depuração ao compilar o aplicativo. É muito mais difícil depurar o código compilado de varejo (uma configuração de versão) do que o código compilado por depuração. Se você precisar usar uma configuração de versão, primeiro desabilite Apenas Meu Código. Para desabilitar essa configuração, escolha **ferramentas**  >  **Opções**  >  **depuração** e, em seguida, desmarque **habilitar apenas meu código**.

- Verifique se o projeto está configurado para produzir [PDBs portáteis](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (que é a configuração padrão) e verifique se os PDBs estão no mesmo local que o dll. Para configurar isso no Visual Studio, clique com o botão direito do mouse no projeto e escolha **Propriedades**  >  **criar**  >  informações **avançadas** de  >  **depuração**.

## <a name="build-and-deploy-the-application"></a>Compilar e implantar o aplicativo

Você pode usar vários métodos para implantar o aplicativo antes da depuração. Por exemplo, você pode:

- Copie as fontes para o computador de destino e crie com ```dotnet build``` o no computador Linux.

- Crie o aplicativo no Windows e, em seguida, transfira os artefatos de compilação para o computador Linux. (Os artefatos de compilação consistem no próprio aplicativo, nos PDBs portáteis, em todas as bibliotecas de tempo de execução das quais ele pode depender e na *.deps.jsno* arquivo.)

Quando o aplicativo for implantado, inicie o aplicativo.

## <a name="attach-the-debugger"></a>Anexar o depurador

Quando o aplicativo estiver em execução no computador Linux, você estará pronto para anexar o depurador.

1. No Visual Studio, escolha **depurar**  >  **anexar ao processo...**.

1. Na lista **tipo de conexão** , selecione **SSH**.

1. Altere o **destino de conexão** para o endereço IP ou nome de host do computador de destino.

   Se você ainda não tiver fornecido credenciais, será solicitado a inserir uma senha e/ou um arquivo de chave privada.

   Não há requisitos de porta a serem configurados, exceto a porta em que o servidor SSH está sendo executado.

1. Localize o processo que você deseja depurar.

   Seu código é executado em um nome de processo exclusivo ou um processo chamado dotnet. Para localizar o processo no qual você está interessado, verifique a coluna **título** , que mostra os argumentos de linha de comando para o processo.

   No exemplo a seguir, você verá uma lista de processos de um computador Linux remoto em um transporte SSH exibido na caixa de diálogo **anexar ao processo** .

   ![Anexar ao processo do Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Escolha **anexar**.

1. Na caixa de diálogo que aparece, selecione o tipo de código que você deseja depurar. Escolha **gerenciado (.NET Core para UNIX)**.

1. Use os recursos de depuração do Visual Studio para depurar o aplicativo.

   No exemplo a seguir, você vê o depurador do Visual Studio interrompido em um ponto de interrupção no código em execução em um computador Linux remoto.

   ![Atingir um ponto de interrupção](media/remote-debug-linux-over-ssh-hit-breakpoint.png)