---
title: Solução de problemas de erros de cliente do Docker no Windows | Microsoft Docs
description: Solucione os problemas encontrados na utilização do Visual Studio para criar e implantar aplicativos Web no Docker ou no Windows usando o Visual Studio 2017.
services: azure-container-service
author: devinb
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.service: multiple
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: devinb
ms.openlocfilehash: a96f9792fa4922a626d4740625d361751242e39b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139076"
---
# <a name="troubleshoot-visual-studio-2017-development-with-docker"></a>Solucionar problemas de desenvolvimento do Visual Studio 2017 com o Docker

Ao trabalhar com Ferramentas do Visual Studio para Docker, você poderá encontrar problemas ao compilar ou depurar seu aplicativo. A seguir estão algumas etapas comuns para solução de problemas.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Compartilhamento de volume não está habilitado. Habilite o compartilhamento de volume nas configurações do Docker CE para Windows (somente contêineres do Linux)

Para resolver esse problema:

1. Clique com o botão direito do mouse em **Docker para Windows** na área de notificação e selecione **Configurações**.
1. Selecione **Unidades Compartilhadas** e compartilhe a unidade do sistema junto com a unidade na qual o projeto reside.

> [!NOTE]
> Se o arquivos aparecer compartilhado, você ainda precisará clicar no link "Redefinir credenciais…" na parte inferior da caixa de diálogo para reabilitar o volume de compartilhamento. Para continuar depois de redefinir as credenciais, talvez seja necessário reiniciar o Visual Studio.

![unidades compartilhadas](media/vs-azure-tools-docker-troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> A versão 15.6 e as versões posteriores do Visual Studio 2017 exibem um aviso quando as **Unidades Compartilhadas** não estão configuradas.

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

## <a name="microsoftdockertools-github-repo"></a>Repositório Microsoft/DockerTools GitHub

Para quaisquer outros problemas que encontrar, consulte problemas do [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).