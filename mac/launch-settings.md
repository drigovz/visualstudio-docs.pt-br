---
title: suporte a launchSettings. JSON
description: Este documento aborda o suporte para launchSettings. JSON no Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715938"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Quando estiver desenvolvendo projetos ASP.NET Core, você poderá configurar como seu projeto deve ser iniciado em cenários de desenvolvimento Personalizando o conteúdo do arquivo launchSettings. JSON. No Visual Studio para Mac, você pode atualizar esse arquivo usando a interface do usuário opções de projeto ou editando-o diretamente. Esse arquivo é o mesmo arquivo de configuração que você pode usar ao executar o Visual Studio no Windows ou a partir da linha de comando por meio de `dotnet`. Esse arquivo é armazenado em seu projeto na pasta Propriedades.

Para obter informações mais detalhadas, consulte [usar vários ambientes em ASP.NET Core](/aspnet/core/fundamentals/environments). Neste artigo, abordaremos como atualizar esse arquivo em Visual Studio para Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Atualizar a configuração inicial usando Visual Studio para Mac

Você pode editar diretamente o arquivo launchSettings. JSON em Visual Studio para Mac, ou pode usar opções de projeto para editá-lo. Para obter as opções de projeto, clique com o botão direito do mouse no projeto e selecione **Opções**.

![Menu de atalho do projeto com "opções" selecionadas](media/vsmac-ctx-proj-options.png)

Selecione **executar** **configurações** de >  > **padrão**.

!["Executar", "configurações" e "padrão" em opções de projeto](media/vsmac-run-config-default.png)

Principalmente, você configurará duas coisas aqui:

 - Variáveis de ambiente
 - URL do aplicativo para o projeto

## <a name="configure-environment-variables"></a>Configurar variáveis de ambiente

Você pode usar a grade para especificar valores para variáveis de ambiente. Essas variáveis de ambiente serão definidas quando você iniciar o aplicativo no Visual Studio para Mac. Ao desenvolver ASP.NET Core aplicativos, você deve estar atento à variável de ambiente de `ASPNETCORE_ENVIRONMENT` especial. Para saber mais, confira [usar vários ambientes no ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configurar a URL inicial

Para configurar a URL com a qual o aplicativo será iniciado, vá para a guia **ASP.NET Core** .

![URL do aplicativo nas opções do projeto](media/vsmac-run-config-default-aspnetcore.png)

Aqui você pode especificar a URL que o aplicativo escutará quando for iniciado.