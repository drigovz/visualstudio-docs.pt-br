---
title: Suporte para o launchSettings.json
description: Este documento aborda o suporte para launchSettings.jsno no Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247923"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Ao desenvolver ASP.NET Core projetos, você pode configurar como seu projeto deve ser iniciado em cenários de desenvolvimento Personalizando o conteúdo da launchSettings.jsno arquivo. No Visual Studio para Mac, você pode atualizar esse arquivo usando a interface do usuário opções de projeto ou editando-o diretamente. Esse arquivo é o mesmo arquivo de configuração que você pode usar ao executar o Visual Studio no Windows ou a partir da linha de comando até `dotnet` . Esse arquivo é armazenado em seu projeto na pasta Propriedades.

Para obter informações mais detalhadas, consulte [usar vários ambientes em ASP.NET Core](/aspnet/core/fundamentals/environments). Neste artigo, abordaremos como atualizar esse arquivo em Visual Studio para Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Atualizar a configuração inicial usando Visual Studio para Mac

Você pode editar diretamente o launchSettings.jsem arquivo no Visual Studio para Mac ou pode usar opções de projeto para editá-lo. Para obter as opções de projeto, clique com o botão direito do mouse no projeto e selecione **Opções**.

![Menu de atalho do projeto com "opções" selecionadas](media/vsmac-ctx-proj-options.png)

Selecione Configurações de **execução**  >  **Configurations**  >  **padrão**.

!["Executar", "configurações" e "padrão" em opções de projeto](media/vsmac-run-config-default.png)

Principalmente, você configurará duas coisas aqui:

- Variáveis de ambiente
- URL do aplicativo para o projeto

## <a name="configure-environment-variables"></a>Configurar variáveis de ambiente

Você pode usar a grade para especificar valores para variáveis de ambiente. Essas variáveis de ambiente serão definidas quando você iniciar o aplicativo no Visual Studio para Mac. Quando estiver desenvolvendo ASP.NET Core aplicativos, você deve estar ciente da `ASPNETCORE_ENVIRONMENT` variável de ambiente especial. Para saber mais, consulte [Usar vários ambientes no ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurar a URL inicial

Para configurar a URL com a qual o aplicativo será iniciado, vá para a guia **ASP.NET Core** .

![URL do aplicativo nas opções do projeto](media/vsmac-run-config-default-aspnetcore.png)

Aqui você pode especificar a URL que o aplicativo escutará quando for iniciado.
