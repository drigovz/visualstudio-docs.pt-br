---
title: Publicar em uma pasta
description: Como publicar um aplicativo Web em uma pasta usando Visual Studio para Mac.
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 640cdf8b9c31bad42f8c5664f3cef44c558e2a3a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493407"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Publicar em uma pasta usando Visual Studio para Mac

Você pode usar a ferramenta de publicação para publicar o console do .NET Core ou os aplicativos ASP.NET Core em uma pasta.

## <a name="prerequisites"></a>Pré-requisitos

- O [Visual Studio 2019 para Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) instalado com o .NET Core está habilitado.
- Um console do .NET Core ou ASP.NET Core projeto. Se você ainda não tiver um projeto, [crie um](./create-new-projects.md).

## <a name="publish-to-folder"></a>Publicar na Pasta

Usando Visual Studio para Mac você pode publicar seus projetos do .NET Core em uma pasta usando a ferramenta de publicação. Depois de publicar em uma pasta, você pode transferir os arquivos para um ambiente diferente. Para publicar uma pasta, siga estas etapas.

 1. Na janela da solução, clique com o botão direito do mouse no projeto e escolha **publicar**.

    ![Menu de contexto Publicar](media/publish-context-menu.png)

 2. Se você já tiver publicado este projeto, o perfil de publicação será exibido no menu. Selecione o perfil de publicação para iniciar o processo de publicação.

 3. Para publicar este projeto em uma pasta pela primeira vez, selecione **Publicar na Pasta**

    ![Menu de contexto Publicar na pasta](media/publish-to-folder-context-menu.png)

 4. A caixa de diálogo **Publicar na pasta** é exibida. Nessa caixa de diálogo, você pode personalizar a pasta em que o projeto será publicado. Você pode usar o botão **Procurar** para fazer isso ou colar em um caminho.

 5. Depois que você clicar em **Publicar** , acontecerão algumas coisas. Primeiro, um perfil de publicação será criado. Um perfil de publicação é um arquivo do MSBuild que é importado para o projeto durante o processo de publicação. Ele contém as propriedades que são usadas durante o processo de publicação. Esses arquivos são armazenados no `Properties/PublishProfiles` e têm a extensão `.pubxml`. Em seguida, o processo de publicação será iniciado. Você pode monitorar o progresso observando a barra de status no Visual Studio para Mac.

    ![Barra de status do IDE com o status Publicar](media/publish-to-folder-status-bar.png)

 6. Depois que a publicação for concluída com êxito, uma janela do Finder abrirá a pasta de publicação. Agora que um perfil de publicação foi criado, ele será exibido no menu de contexto de publicação.

    ![Menu de contexto de publicação com o perfil da pasta](media/publish-context-menu-with-folder-profile.png)

 7. Para publicar o projeto novamente com as mesmas configurações, clique no perfil no menu de contexto de publicação.

## <a name="customize-publish-options"></a>Personalizar as opções de publicação

Para alterar o nome do perfil de publicação (que é exibido no menu de contexto de publicação), renomeie o arquivo de perfil de publicação. Não altere a extensão do arquivo (`.pubxml`).

Para alterar o caminho da pasta de publicação, abra o perfil de publicação e edite o valor de `publishUrl`.

Para alterar a configuração de build que é usada, altere a propriedade `LastUsedBuildConfiguration` no perfil de publicação.