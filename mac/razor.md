---
title: Criar aplicativos web Razor
description: Fornece informações sobre o suporte ao Razor em ASP.NET aplicativos Core no Visual Studio para Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715881"
---
# <a name="create-razor-web-apps"></a>Criar aplicativos web Razor

Este guia oferece uma introdução para criar seu primeiro aplicativo web Razor. Para obter uma orientação mais detalhada, consulte [Introdução a Páginas de Navalha em ASP.NET Núcleo](/aspnet/core/razor-pages/index).

O Visual Studio para Mac oferece suporte à edição de Razor, inclusive IntelliSense e realce de sintaxe em arquivos *.cshtml*. A novidade no Visual Studio 2019 para Mac 8.3+ é a capacidade de ter o IntelliSense consciente de contexto dentro de um arquivo Razor, para que você receba o IntelliSense que corresponde ao idioma que você está editando atualmente dentro de um documento.

![Edição de Razor no Visual Studio para Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Como criar um novo projeto do Razor

1. Na tela de boas-vindas, selecione **Novo** para criar um novo projeto:

   ![Novo projeto do Visual Studio para Mac](media/razor-new.png)
1. Na caixa de diálogo **Do Novo Projeto,** vá para o**aplicativo Web do** **aplicativo** >  **.NET Core** > e selecione **Next**:

   ![Modelo de projeto do Razor](media/razor-new-project1.png)
1. Selecione sua estrutura de destino .NET Core (recomendamos a versão 2.2 ou posterior) e selecione **Next**. Escolha um nome para o seu projeto e adicione suporte ao Git, se necessário. Selecione **Criar** para criar o cluster.

   ![Nome do projeto do Razor](media/razor-new-project2.png)

   Visual Studio for Mac abre seu projeto na janela de layout Código.
1. Execute o projeto sem depuração usando **Command+Option+F5**.

   O Visual Studio inicia o `https://localhost:5001` [Kestrel,](/aspnet/core/fundamentals/servers/kestrel)abre um navegador para e exibe seu primeiro aplicativo web Razor.

   ![Aplicativo Web do Razor no Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Anatomia do projeto

Os aplicativos web razor incluem os seguintes componentes.

### <a name="pages-folder"></a>Pasta Páginas

Esta pasta contém as páginas da Web de um projeto, juntamente com o código-traseiro para cada um:
   - Um arquivo * \*.cshtml* para a marcação HTML e sintaxe de navalha.
   - Um arquivo * \*.cshtml.cs* para o seu código C# para lidar com eventos de página.

Arquivos de suporte têm nomes que começam com um sublinhado. Por exemplo, o arquivo _Layout.cshtml configura os elementos de interface do usuário comuns a todas as páginas. Este arquivo configura o menu de navegação na parte superior da página e o aviso de direitos autorais na parte inferior. Saiba mais em [Layout no ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Configurações de inicialização

O arquivo *launchSettings.json* contém as configurações do IIS, a URL do aplicativo e outras configurações relacionadas.

### <a name="app-settings"></a>Configurações do aplicativo

O arquivo *appSettings.json* contém dados de configuração, como strings de conexão.

Para obter mais informações sobre a configuração, consulte o [guia Configuração em ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Pasta wwwroot

Esta pasta contém arquivos estáticos, como arquivos HTML, JavaScript e CSS. Saiba mais em [Arquivos estáticos no ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Module.vb

Este arquivo contém o ponto de entrada do programa. Saiba mais em [Host da Web do ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Este arquivo contém código que configura o comportamento do aplicativo, como se o aplicativo requer consentimento para cookies. Saiba mais em [Inicialização de aplicativos no ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Confira também

Para obter um guia mais abrangente para criar aplicativos web Razor, consulte [Introdução a páginas de barbear em ASP.NET Core](/aspnet/core/razor-pages/index).
