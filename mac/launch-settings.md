---
title: suporte a launchSettings.json
description: Este documento abrange o suporte para lançamentoSettings.json no Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715938"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Quando você está desenvolvendo projetos ASP.NET Core, você pode configurar como seu projeto deve ser iniciado em cenários de desenvolvimento, personalizando o conteúdo do arquivo launchSettings.json. No Visual Studio para Mac, você pode atualizar este arquivo usando a ui opções do projeto ou editando-o diretamente. Este arquivo é o mesmo arquivo de configuração que você pode `dotnet`usar ao executar o Visual Studio no Windows ou da linha de comando através de . Este arquivo é armazenado em seu projeto na pasta Propriedades.

Para obter informações mais [detalhadas,](/aspnet/core/fundamentals/environments)consulte Usar vários ambientes em ASP.NET Core . Neste artigo, vamos cobrir como atualizar este arquivo no Visual Studio para Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Atualize a configuração inicial usando o Visual Studio para Mac

Você pode editar diretamente o arquivo launchSettings.json no Visual Studio for Mac, ou pode usar opções de projeto para editá-lo. Para chegar às opções do projeto, clique com o botão direito do mouse no projeto e selecione **Opções**.

![Menu de atalho do projeto com "Opções" selecionada](media/vsmac-ctx-proj-options.png)

Selecione 'Executar**configurações** > **padrão ''Executar'.** **Run** > 

!["Executar", "Configurações" e "Padrão" nas opções do projeto](media/vsmac-run-config-default.png)

Primeiramente, você vai configurar duas coisas aqui:

 - Variáveis de ambiente
 - URL do aplicativo para o projeto

## <a name="configure-environment-variables"></a>Configurar variáveis de ambiente

Você pode usar a grade para especificar valores para variáveis de ambiente. Essas variáveis de ambiente serão definidas quando você iniciar sua aplicação no Visual Studio for Mac. Quando você está desenvolvendo aplicações ASP.NET Core, você `ASPNETCORE_ENVIRONMENT` deve estar ciente da variável ambiente especial. Para saber mais, [consulte Use vários ambientes em ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Configure o URL inicial

Para configurar a URL com a que o aplicativo será iniciado, vá para a guia **ASP.NET Core.**

![URL do aplicativo nas opções de projeto](media/vsmac-run-config-default-aspnetcore.png)

Aqui você pode especificar a URL que o aplicativo ouvirá quando for iniciado.