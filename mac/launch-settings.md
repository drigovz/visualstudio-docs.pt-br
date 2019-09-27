---
title: suporte a launchSettings. JSON
description: Este documento aborda o suporte para launchSettings. JSON no Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: 7135dd05c687e3caed3ee64618ff71c093f4cd63
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322587"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Quando estiver desenvolvendo projetos ASP.NET Core, você poderá configurar como seu projeto deve ser iniciado em cenários de desenvolvimento Personalizando o conteúdo do arquivo launchSettings. JSON. No Visual Studio para Mac, você pode atualizar esse arquivo usando a interface do usuário opções de projeto ou editando-o diretamente. Esse arquivo é o mesmo arquivo de configuração que você pode usar ao executar o Visual Studio no Windows ou a partir da `dotnet`linha de comando até. Esse arquivo é armazenado em seu projeto na pasta Propriedades.

Para obter informações mais detalhadas, consulte [usar vários ambientes em ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). Neste artigo, abordaremos como atualizar esse arquivo em Visual Studio para Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Atualizar a configuração inicial usando Visual Studio para Mac

Você pode editar diretamente o arquivo launchSettings. JSON em Visual Studio para Mac, ou pode usar opções de projeto para editá-lo. Para obter as opções de projeto, clique com o botão direito do mouse no projeto e selecione **Opções**.

![Menu de atalho do projeto com "opções" selecionadas](media/vsmac-ctx-proj-options.png)

Selecione > configuraçõesde > execução**padrão**.

!["Executar", "configurações" e "padrão" em opções de projeto](media/vsmac-run-config-default.png)

Principalmente, você configurará duas coisas aqui:

 - Variáveis de ambiente
 - URL do aplicativo para o projeto

## <a name="configure-environment-variables"></a>Configurar variáveis de ambiente

Você pode usar a grade para especificar valores para variáveis de ambiente. Essas variáveis de ambiente serão definidas quando você iniciar o aplicativo no Visual Studio para Mac. Quando estiver desenvolvendo ASP.NET Core aplicativos, você deve estar ciente da variável de ambiente `ASPNETCORE_ENVIRONMENT` especial. Para saber mais, confira [usar vários ambientes no ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurar a URL inicial

Para configurar a URL com a qual o aplicativo será iniciado, vá para a guia **ASP.NET Core** .

![URL do aplicativo nas opções do projeto](media/vsmac-run-config-default-aspnetcore.png)

Aqui você pode especificar a URL que o aplicativo escutará quando for iniciado.