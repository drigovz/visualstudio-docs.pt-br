---
title: Crie aplicativos web Blazor
description: Fornece informações sobre o suporte ao Blazor em ASP.NET aplicativos Core no Visual Studio para Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737582"
---
# <a name="create-blazor-web-apps"></a>Crie aplicativos web Blazor

Este guia oferece uma introdução para criar o seu primeiro aplicativo web Blazor. Para obter uma orientação mais aprofundada, consulte [Introdução ao ASP.NET Core Blazor](/aspnet/core/blazor/index).

Visual Studio para Mac (começando pela versão 8.4) inclui suporte para o desenvolvimento e publicação ASP.NET aplicativos Core Blazor Server. Blazor é uma estrutura para construir uma web ui interativa do lado do cliente com a .NET, que oferece as seguintes vantagens para desenvolvedores web:

* escreva o código em C# em vez de JavaScript.
* Aproveite o ecossistema .NET existente das bibliotecas .NET.
* Compartilhe a lógica de aplicativo entre o servidor e o cliente.
* Beneficie-se de . Desempenho, confiabilidade e segurança da NET.
* Mantenha-se produtivo com o Visual Studio no PC, Linux e macOS.
* Crie um conjunto comum de linguagens, estruturas e ferramentas que são estáveis, com recursos avançados e fáceis de usar.

## <a name="creating-a-new-blazor-project"></a>Criando um novo projeto Blazor

1. Na **janela Iniciar,** selecione **Novo** para criar um novo projeto:

   ![Visual Studio para Mac Start Window com nova seleção em destaque](media/blazor-new-project.png)
1. Na caixa de diálogo **do Novo Projeto,** selecione **.NET** > **Core App** > **Blazor Server App** e selecione **Next**: ![Escolha um modelo para o seu novo diálogo de projeto com o modelo do aplicativo Blazor Server selecionado](media/blazor-project-template.png)

1. Selecione .NET Core 3.1 como o framework de destino e selecione **'Seguinte**' 
   ![Configure a nova caixa de diálogo do Aplicativo Blazor Server exibida com o Target Framework selecionado para .NET Core 3.1](media/blazor-select-target-framework.png)

1. Escolha um nome para o seu projeto e adicione o suporte ao Git, se desejar. Selecione **Criar** para criar o cluster.
   ![BConfigure sua nova caixa de diálogo blazor server app exibida ao inserir Nome do Projeto](media/blazor-name-project.png)

   Visual Studio for Mac abre seu projeto na janela de layout Código.
1. Selecione **Executar** > **iniciar sem depuração** para executar o aplicativo.

   O Visual Studio inicia o `https://localhost:5001` [Kestrel,](/aspnet/core/fundamentals/servers/kestrel)abre um navegador para e exibe seu aplicativo web Blazor.

   ![Aplicativo web Blazor em Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Suporte blazor no Visual Studio para Mac

Visual Studio para Mac (começando pela versão 8.4) inclui novos recursos para ajudá-lo a criar novos projetos de servidor Blazor. Além disso, ele fornece o suporte padrão que você esperaria, como construir, executar e depurar projetos Blazor. 

No passo a passo acima, vimos como o modelo de projeto do Aplicativo Blazor Server ajuda você a criar um novo projeto do Aplicativo Blazor Server. Vamos dar uma olhada em alguns dos recursos adicionais no Visual Studio para Mac para apoiar o desenvolvimento de projetos de servidor Blazor.

### <a name="editor-support-for-razor-files"></a>Suporte ao editor para arquivos *.razor*
Visual Studio for Mac inclui suporte para editar arquivos .razor - a maioria dos arquivos que você estará usando ao criar aplicativos Blazor. A versão do Windows e Mac do IDE compartilham o mesmo editor para arquivos .razor. Você verá suporte completo de coloração e conclusão para seus arquivos .razor, incluindo conclusões para componentes razor declarados no projeto.

![Visual Studio para mac janela editor mostrando Intellisense para Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publicando aplicativos Blazor para o Serviço de Aplicativos Do Azure
Você também pode publicar aplicativos Blazor diretamente no Azure App Service. Se você não tem uma conta no Azure para executar seu aplicativo Blazor no Azure, você sempre pode [se inscrever para um gratuito aqui](https://azure.microsoft.com/free) que também vem 12 meses de serviços populares gratuitos, $200 créditos gratuitos do Azure e mais de 25 serviços sempre gratuitos.

![Visual Studio para Mac mostrando a experiência de publicação do Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomia do projeto

Os aplicativos web Blazor incluem alguns diretórios e arquivos por padrão. Como você está começando, aqui estão os principais que você precisa estar familiarizado:

### <a name="pages-folder"></a>Pasta Páginas

Esta pasta contém as páginas da Web de um projeto, que usam uma extensão de arquivo *.razor.*

### <a name="shared-folder"></a>Pasta compartilhada

Esta pasta inclui componentes compartilhados, também usando a extensão *.razor.* Você verá que isso inclui *MainLayout.razor*, que é usado para definir layout comum em todo o aplicativo. Ele também inclui o componente *NavMenu.razor* compartilhado, que é usado em todas as páginas. Se você estiver criando componentes reutilizáveis, eles irão para a pasta **Compartilhada.**

### <a name="app-settings"></a>Configurações do aplicativo

O arquivo *appSettings.json* contém dados de configuração, como strings de conexão.

Para obter mais informações sobre a configuração, consulte o [guia Configuração em ASP.NET](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Pasta wwwroot

Esta pasta contém arquivos estáticos, como arquivos HTML, JavaScript e CSS. Saiba mais em [Arquivos estáticos no ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Module.vb

Este arquivo contém o ponto de entrada do programa. Saiba mais em [Host da Web do ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Este arquivo contém código que configura o comportamento do aplicativo, como se o aplicativo requer consentimento para cookies. Saiba mais em [Inicialização de aplicativos no ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Resumo
Neste tutorial, você viu como criar um novo Aplicativo Blazor Server no Visual Studio para Mac, e aprendeu sobre alguns dos recursos que o Visual Studio for Mac oferece para ajudá-lo a criar aplicativos Blazor.

## <a name="see-also"></a>Confira também

Para obter um guia mais abrangente para criar aplicativos web Blazor, consulte [Introdução a ASP.NET Core Blazor](/aspnet/core/blazor/index).
