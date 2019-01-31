---
title: Configurar um host do Docker com o VirtualBox | Microsoft Docs
description: Instruções passo a passo para configurar uma instância de Docker padrão usando a máquina Docker e o VirtualBox
services: azure-container-service
documentationcenter: na
author: mlearned
manager: jillfra
ms.assetid: 0b1335a2-7720-42a8-8260-4e06fc00c9f6
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 06/08/2016
ms.author: mlearned
ms.openlocfilehash: a3c02d59021f7596c4c754e185782c591b71fd11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139066"
---
# <a name="configure-a-docker-host-with-virtualbox"></a>Configurar um host do Docker com o VirtualBox
## <a name="overview"></a>Visão geral
Este artigo orienta você pela configuração de uma instância de Docker padrão usando a máquina Docker e o VirtualBox.
Se você estiver usando o [Docker para Windows](https://www.docker.com/products/docker-desktop), essa configuração não é necessária.

## <a name="prerequisites"></a>Pré-requisitos
As ferramentas a seguir precisam ser instaladas.

* [Caixa de Ferramentas do Docker](https://github.com/docker/toolbox/releases)

## <a name="configuring-the-docker-client-with-windows-powershell"></a>Configurando o cliente Docker com o Windows PowerShell
Para configurar um cliente Docker, apenas abra o Windows PowerShell e execute as seguintes etapas:

1. Crie uma instância de host do docker padrão.

    ```PowerShell
    docker-machine create --driver virtualbox default
    ```
2. Verifique se a instância padrão está configurada e em execução. (Você deve ver uma instância chamada “padrão” em execução.

    ```PowerShell
    docker-machine ls
    ```

    ![saída do docker-machine Is](media/vs-azure-tools-docker-setup/docker-machine-ls.png)
3. Defina o padrão como o host atual e configure seu shell.

    ```PowerShell
    docker-machine env default | Invoke-Expression
    ```
4. Exiba os contêineres do Docker ativo. A lista deve estar vazia.

    ```PowerShell
    docker ps
    ```

    ![saída do docker ps](media/vs-azure-tools-docker-setup/docker-ps.png)

> [!NOTE]
> Sempre que você reinicializar o computador de desenvolvimento, precisará reiniciar o host do Docker local.
> Para fazer isso, envie o seguinte comando em um prompt de comando: `docker-machine start default`.
