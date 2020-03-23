---
title: Depurar aplicativos em um contêiner Docker local | Microsoft Docs
description: Aprenda a modificar um aplicativo que está sendo executado em um contêiner Docker local, atualize o contêiner via Editar e Atualizar e, em seguida, defina pontos de interrupção de depuração.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916528"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Depurar aplicativos em um contêiner Docker local

O Visual Studio fornece uma maneira consistente de desenvolver contêineres Docker e validar seu aplicativo localmente. Você pode executar e depurar seus aplicativos em contêineres Linux ou Windows em execução em sua área de trabalho local do Windows com o Docker instalado, e você não precisa reiniciar o contêiner cada vez que fizer uma alteração de código.

Este artigo ilustra como usar o Visual Studio para iniciar um aplicativo em um contêiner Docker local, fazer alterações e, em seguida, atualizar o navegador para ver as alterações. Este artigo também mostra como definir pontos de interrupção para depuração de aplicativos contêiner. Os tipos de projeto suportados incluem aplicativos de web e console .NET Framework e .NET Core. Neste artigo, usamos ASP.NET aplicativos web Core e aplicativos de console .NET Framework.

Se você já tem um projeto de um tipo suportado, o Visual Studio pode criar um Arquivo Docker e configurar seu projeto para executar em um contêiner. Consulte [Ferramentas de Contêiner no Visual Studio](overview.md).

## <a name="prerequisites"></a>Pré-requisitos

Para depurar aplicativos em um contêiner Docker local, as seguintes ferramentas devem ser instaladas:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) com a carga de trabalho de Desenvolvimento Web instalada

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com a carga de trabalho de Desenvolvimento Web instalada

::: moniker-end

Para executar contêineres Docker localmente, você deve ter um cliente Docker local. Você pode usar a [Caixa de Ferramentas Docker,](https://www.docker.com/products/docker-toolbox)que requer que o Hyper-V seja desativado. Você também pode usar [o Docker para Windows](https://www.docker.com/get-docker), que usa Hyper-V e requer windows 10.

Os contêineres Docker estão disponíveis para projetos .NET Framework e .NET Core. Vamos analisar dois exemplos. Primeiro, olhamos para um aplicativo web .NET Core. Em seguida, olhamos para um aplicativo de console .NET Framework.

## <a name="create-a-web-app"></a>Criar um aplicativo Web

Se você tiver um projeto e adicionar o suporte ao Docker conforme descrito na [visão geral,](overview.md)pule esta seção.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Editar seu código e atualizar

Para iterar rapidamente as alterações, você pode iniciar sua aplicação em um contêiner. Em seguida, continue a fazer alterações, vendo-as como você faria com o IIS Express.

1. Certifique-se de que o Docker está configurado para usar o tipo de contêiner (Linux ou Windows) que você está usando. Clique com o botão direito do mouse no ícone Docker na Barra de Tarefas e escolha **Mudar para contêineres Linux** ou mudar para **contêineres do Windows** conforme apropriado.

1. (.Núcleo NET 3 e somente posteriormente) Editar seu código e atualizar o site em execução como descrito nesta seção não está habilitado nos modelos padrão em .NET Core >= 3.0. Para habilitá-lo, adicione o pacote NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). Em *Startup.cs,* adicione uma chamada `IMvcBuilder.AddRazorRuntimeCompilation` ao método `ConfigureServices` de extensão ao código no método. Você só precisa disso ativado no modo DEBUG, então codificá-lo da seguinte forma:

    ```csharp
    public IWebHostEnvironment Env { get; set; }
    
    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();
    
    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif
    
        // code omitted for brevity
    }
    ```

   Para obter mais informações, consulte [a compilação de arquivos Razor em ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1).

1. Definir **configuração da solução** para **depurar**. Em seguida, **pressione Ctrl**+**F5** para construir sua imagem de Docker e executá-la localmente.

    Quando a imagem do contêiner é construída e em execução em um contêiner Docker, o Visual Studio inicia o aplicativo web em seu navegador padrão.

1. Vá para a página *Índice.* Vamos fazer alterações nesta página.
1. Retorne ao Visual Studio e abra *Index.cshtml*.
1. Adicione o conteúdo HTML a seguir ao final do arquivo e, em seguida, salve as alterações.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Na janela de saída, quando a compilação .NET estiver concluída e você ver as seguintes linhas, volte para o seu navegador e atualize a página:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

As alterações foram aplicadas.

### <a name="debug-with-breakpoints"></a>Depurar com pontos de interrupção

Muitas vezes, as mudanças requerem uma inspeção adicional. Você pode usar os recursos de depuração do Visual Studio para esta tarefa.

1. No Visual Studio, *abra Index.cshtml.cs*.
2. Substitua o `OnGet` conteúdo do método pelo seguinte código:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. À esquerda da linha de código, defina um ponto de ruptura.
4. Para começar a depurar e acertar o ponto de partida, pressione F5.
5. Mude para o Visual Studio para ver o ponto de partida. Inspecione os valores.

   ![Ponto de interrupção](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Criar um aplicativo de console .NET Framework

Quando você usa projetos de aplicativo de console .NET Framework, a opção de adicionar suporte ao Docker sem orquestração não é suportada. Você ainda pode usar o seguinte procedimento, mesmo se estiver usando apenas um único projeto Docker.

1. Crie um novo projeto de aplicativo .NET Framework Console.
1. No Solution Explorer, clique com o botão direito do mouse no nó do projeto e, em seguida, **selecione Adicionar** > **suporte de orquestração de contêiner**.  Na caixa de diálogo que aparece, selecione **'Compor'** Um arquivo Docker é adicionado ao seu projeto e um projeto do Docker Compose com arquivos de suporte associados é adicionado.

### <a name="debug-with-breakpoints"></a>Depurar com pontos de interrupção

1. No Solution Explorer, *abra Program.cs*.
2. Substitua o `Main` conteúdo do método pelo seguinte código:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Defina um ponto de interrupção à esquerda da linha de código.
4. Pressione F5 para começar a depurar e atingir o ponto de ruptura.
5. Mude para o Visual Studio para visualizar o ponto de partida e inspecionar valores.

   ![Ponto de interrupção](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Reutilização de contêineres

Durante o ciclo de desenvolvimento, o Visual Studio reconstrói apenas as imagens do contêiner e o próprio contêiner quando você altera o arquivo Docker. Se você não alterar o Arquivo Docker, o Visual Studio reutiliza o contêiner de uma execução anterior.

Se você modificou manualmente seu recipiente e deseja reiniciar com uma imagem limpa do recipiente, use o comando **Build** > **Clean** no Visual Studio e, em seguida, construa normalmente.

## <a name="troubleshoot"></a>Solucionar problemas

Aprenda a [solucionar problemas no desenvolvimento do Visual Studio Docker](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Próximas etapas

Obtenha mais detalhes lendo [Como o Visual Studio constrói aplicativos contêiner.](container-build.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Mais informações sobre o Docker com o Visual Studio, Windows e Azure

* Saiba mais sobre [o desenvolvimento de contêineres com o Visual Studio](/visualstudio/containers).
* Para construir e implantar um contêiner Docker, consulte [a integração Docker para a Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Para obter um índice de artigos do Windows Server e do Nano Server, consulte [as informações do contêiner do Windows](/virtualization/windowscontainers/).
* Conheça [o Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) e revise a documentação do [Azure Kubernetes Service](/azure/aks).
