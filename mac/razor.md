---
title: Razor
description: Informações sobre o suporte para Razor em aplicativos do ASP.NET Core no Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: 9e5a3f61ee7065a0615a381bdcc03dafc3566893
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691263"
---
# <a name="razor"></a>Razor

O Visual Studio para Mac oferece suporte à edição de Razor, inclusive IntelliSense e realce de sintaxe em arquivos *.cshtml*.

![Edição de Razor no Visual Studio para Mac](media/razor-editor.png)

Este guia oferece uma introdução à criação do seu primeiro aplicativo Web do Razor. Confira um guia mais aprofundado em [Razor Pages na documentação do .NET Core](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Como criar um novo projeto do Razor

* Na tela de boas-vindas, selecione **Novo** para criar um novo projeto:

![Novo projeto do Visual Studio para Mac](media/razor-new.png)

* Na caixa de diálogo Novo Projeto, navegue para **.NET Core** > **Aplicativo** > **Aplicativo Web** e selecione o botão **Avançar**:

![Modelo de projeto do Razor](media/razor-new-project1.png)

* Selecione o .NET Core Target Framework necessário (é recomendado o 2.2 ou posterior) e selecione **Avançar**.  Escolha um nome para o seu projeto e adicione suporte ao git, se necessário. Selecione **Criar** para criar o cluster.

![Nome do projeto do Razor](media/razor-new-project2.png)

O Visual Studio para Mac abrirá seu projeto no layout de Programação.

* Execute o projeto sem depurar usando **Cmd-Opt-F5**

O Visual Studio iniciará o [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), inicializará um navegador para `https://localhost:5001` e exibirá seu primeiro aplicativo Web do Razor:

![Aplicativo Web do Razor no Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomia do projeto

Os aplicativos Web do Razor consistem nos seguintes componentes:

### <a name="pages-folder"></a>Pasta Páginas

A pasta Páginas dentro do projeto é onde as páginas da Web podem ser encontradas com o code-behind de cada uma:
* Um arquivo * *.cshtml* para a marcação HTML e sintaxe Razor.
* Um arquivo * *.cshtml.cs* para seu code-behind C# para manipular eventos de página.

Arquivos de suporte têm nomes que começam com um sublinhado. Por exemplo, o arquivo _Layout.cshtml configura os elementos de interface do usuário comuns a todas as páginas. Esse arquivo define o menu de navegação na parte superior da página e a notificação de direitos autorais na parte inferior da página. Saiba mais em [Layout no ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Configurações de inicialização

O arquivo *launchSettings.json* contém as configurações do IIS, o URL do aplicativo e outras configurações relacionadas.

### <a name="app-settings"></a>Configurações do aplicativo

O arquivo *appSettings,json* contém dados de configuração, como sequências de conexão.

Saiba mais sobre configuração no guia [Configuração no ASP.NET](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Pasta wwwroot

Contém os arquivos estáticos, como arquivos HTML, arquivos JavaScript e arquivos CSS. Saiba mais em [Arquivos estáticos no ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Module.vb

Contém o ponto de entrada para o programa. Saiba mais em [Host da Web do ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Contém o código que configura o comportamento do aplicativo, como se ele requer o consentimento para cookies. Saiba mais em [Inicialização de aplicativos no ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Confira também

Confira um guia mais abrangente sobre como criar aplicativos Web do Razor em [Introdução ao Razor Pages no ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
