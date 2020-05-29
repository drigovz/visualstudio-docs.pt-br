---
title: Criar aplicativos Web mais podestas
description: Fornece informações sobre o suporte mais incrivelmente em aplicativos ASP.NET Core no Visual Studio para Mac.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: 978e3676d587bcd54a8e9d0b8b81f5d6c52a92bc
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180267"
---
# <a name="create-blazor-web-apps"></a>Criar aplicativos Web mais podestas

Este guia oferece uma introdução à criação do seu primeiro aplicativo Web de mais incrivelmente. Para obter diretrizes mais detalhadas, consulte [introdução ao ASP.NET Core](/aspnet/core/blazor/index)mais alto.

ASP.NET Core mais incrivelmente dá suporte a duas opções de hospedagem diferentes; Servidor e Webassembly de mais incrivelmente. O Visual Studio para Mac dá suporte a ambos os modelos de hospedagem. O Visual Studio para Mac 8.4 + dá suporte a um servidor mais incrivelmente e o Visual Studio para Mac 8.6 + dá suporte a ambos. Para obter mais informações sobre modelos de hospedagem mais incrivelmente, confira [ASP.NET Core modelos de hospedagem mais incrivelmente ](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). O suporte para depuração de projetos de Webassembly mais povelativos em Visual Studio para Mac será lançado em uma versão posterior a 8,6.

O que é mais incrivelmente? O mais vantajoso é uma estrutura para a criação de interface do usuário da Web interativa do lado do cliente com o .NET, que oferece as seguintes vantagens aos desenvolvedores da Web:

* escreva o código em C# em vez de JavaScript.
* Aproveite o ecossistema .NET existente das bibliotecas .NET.
* Compartilhe a lógica de aplicativo entre o servidor e o cliente.
* Beneficie-se do. Desempenho, confiabilidade e segurança da rede.
* Mantenha-se produtivo com o Visual Studio em PC, Linux e macOS.
* Crie um conjunto comum de linguagens, estruturas e ferramentas que são estáveis, com recursos avançados e fáceis de usar.

## <a name="creating-a-new-blazor-server-project"></a>Criando um novo projeto de servidor de mais novos

1. Na **janela iniciar**, selecione **novo** para criar um novo projeto:

   ![Visual Studio para Mac janela inicial com a nova seleção realçada](media/blazor-new-project.png)
1. Na caixa de diálogo **novo projeto** , selecione aplicativo do servidor **.NET Core** > **App** > **Blazor Server App** e selecione **Avançar**: ![ escolha um modelo para a caixa de diálogo novo projeto com o modelo de aplicativo de servidor mais novo selecionado](media/blazor-project-template.png)

1. Selecione .NET Core 3,1 como a estrutura de destino e, em seguida, selecione **Avançar**. 
   ![Configure sua nova caixa de diálogo de aplicativo de servidor do mais novo, exibida com a estrutura de destino selecionada para o .NET Core 3,1](media/blazor-select-target-framework.png)

1. Escolha um nome para seu projeto e adicione o suporte do git, se desejado. Selecione **Criar** para criar o cluster.
   ![BConfigure a caixa de diálogo do novo aplicativo de servidor mais incrivelmente exibida ao inserir o nome do projeto](media/blazor-name-project.png)

   Visual Studio para Mac abre seu projeto na janela de layout de código.
1. Selecione **executar**  >  **Iniciar sem depuração** para executar o aplicativo.

   O Visual Studio inicia o [Kestrel](/aspnet/core/fundamentals/servers/kestrel), abre um navegador para `https://localhost:5001` e exibe o seu aplicativo Web mais incrivelmente.

   ![Aplicativo Web mais incrivelmente no Safari](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Suporte mais incrivelmente no Visual Studio para Mac

A Visual Studio para Mac (a partir da versão 8,4) inclui novos recursos para ajudá-lo a criar novos projetos de servidor mais avançados. Além de isso, ele fornece o suporte padrão que você esperaria, como a criação, a execução e a depuração de projetos mais elaborados. No Visual Studio para Mac suporte 8,6 para criação, criação e execução de projetos Webassembly de maior e/.

No passo a passos acima, vimos como o modelo de projeto de aplicativo de servidor mais recente ajuda você a criar um novo projeto de aplicativo de servidor mais recente. Vamos dar uma olhada em alguns dos recursos adicionais do Visual Studio para Mac para dar suporte ao desenvolvimento de projetos mais incrivelmente.

### <a name="editor-support-for-razor-files"></a>Suporte do editor para arquivos *. Razor*
O Visual Studio para Mac inclui suporte para edição de arquivos. Razor-a maioria dos arquivos que você usará ao criar aplicativos mais podestas. A versão do Windows e Mac do IDE compartilham o mesmo editor para arquivos. Razor. Você verá a colorização completa e o suporte de conclusão para seus arquivos. Razor, incluindo as conclusões dos componentes do Razor declarados no projeto.

![Janela do editor de Visual Studio para Mac mostrando o IntelliSense para um mais incrivelmente](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Publicando aplicativos de mais incrivelmente em Azure App serviço
Você também pode publicar aplicativos mais incrivelmente diretamente no serviço Azure App. Se você não tiver uma conta do Azure para executar seu aplicativo mais novo no Azure, você sempre poderá [se inscrever em um aqui gratuito](https://azure.microsoft.com/free) que também vem de 12 meses de serviços populares gratuitos, $200 créditos gratuitos do Azure e mais de 25 serviços sempre gratuitos.

![Visual Studio para Mac mostrando a experiência de publicação do Azure](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Anatomia do projeto

Os aplicativos Web mais incrivelmente incluem alguns diretórios e arquivos por padrão. Como você está começando, aqui estão os principais que você precisará estar familiarizados com:

### <a name="pages-folder"></a>Pasta Páginas

Esta pasta contém as páginas da Web de um projeto, que usam uma extensão de arquivo *. Razor* .

### <a name="shared-folder"></a>Pasta compartilhada

Essa pasta inclui componentes compartilhados, também usando a extensão *. Razor* . Você verá que isso inclui o *MainLayout. Razor*, que é usado para definir o layout comum em todo o aplicativo. Ele também inclui o componente *NavMenu. Razor* compartilhado, que é usado em todas as páginas. Se você estiver criando componentes reutilizáveis, eles irão para a pasta **compartilhada** .

### <a name="app-settings"></a>Configurações de aplicativo

O arquivo *appSettings. JSON* contém dados de configuração, como cadeias de conexão.

Para obter mais informações sobre a configuração, consulte a [configuração no guia do ASP.net](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Pasta wwwroot

Essa pasta contém arquivos estáticos, como HTML, JavaScript e arquivos CSS. Saiba mais em [Arquivos estáticos no ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Module.vb

Esse arquivo contém o ponto de entrada para o programa. Saiba mais em [Host da Web do ASP.NET Core](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Esse arquivo contém um código que configura o comportamento do aplicativo, como se o aplicativo requer consentimento para cookies. Saiba mais em [Inicialização de aplicativos no ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="summary"></a>Resumo
Neste tutorial, você viu como criar um novo aplicativo de servidor de mais novos Visual Studio para Mac e aprendeu sobre alguns dos recursos que Visual Studio para Mac oferece para ajudá-lo a criar aplicativos mais avançados.

## <a name="see-also"></a>Veja também

Para obter um guia mais abrangente para criar aplicativos Web mais completos, consulte [introdução ao ASP.NET Core](/aspnet/core/blazor/index)mais grande.
