---
title: suporte a launchSettings. JSON
description: Este documento aborda o suporte para launchSettings. JSON no Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213755"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Ao desenvolver ASP.NET Core projetos, você pode configurar como seu projeto deve ser iniciado em cenários de desenvolvimento Personalizando o conteúdo do `launchSettings.json` arquivo. No Visual Studio para Mac, você pode atualizar esse arquivo usando a interface do usuário opções de projeto ou editando `launchSettings.json` o arquivo diretamente. Esse arquivo é o mesmo arquivo de configuração que pode ser usado ao executar o Visual Studio no Windows ou a partir da `dotnet`linha de comando usando. Esse arquivo é armazenado em seu projeto `Properties` na pasta.

Para obter informações mais detalhadas, você pode ir para [usar vários ambientes no ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). Neste documento, abordaremos como atualizar esse arquivo em Visual Studio para Mac.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Atualizando a configuração de início usando Visual Studio para Mac

Você pode editar diretamente o `launchSettings.json` no Visual Studio para Mac ou pode usar opções de projeto para editá-lo. Para obter as opções de projeto, clique com o botão direito do mouse no projeto e selecione opções. Consulte a imagem abaixo.

![opções do menu de contexto do projeto selecionadas](media/vsmac-ctx-proj-options.png)

Quando chegar a essa caixa de diálogo, vá para executar configurações de > > padrão.

![executar configurações padrão](media/vsmac-run-config-default.png)

Há principalmente duas coisas que você configurará aqui.

 - Variáveis de ambiente definidas em iniciar
 - URL inicial do projeto

## <a name="configure-environment-variables"></a>Configurar variáveis de ambiente

Você pode usar a grade para especificar valores para variáveis de ambiente. Essas variáveis de ambiente serão definidas quando você iniciar seu aplicativo no Visual Studio para Mac. Ao desenvolver ASP.NET Core aplicativos, você deve estar ciente da variável de `ASPNETCORE_ENVIRONMENT` ambiente especial. Para saber mais, confira [usar vários ambientes no ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Configurar URL inicial

Para configurar a URL com a qual o aplicativo será iniciado, acesse a guia ASP.NET Core.

![URL de início das opções de proj](media/vsmac-run-config-default-aspnetcore.png)

Aqui você pode especificar as URLs que o aplicativo escutará quando for iniciado.