---
title: Aplicativo de vários contêineres com Docker Compose
description: Saiba como gerenciar mais de um contêiner e se comunicar entre eles no Visual Studio para Mac
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: f2c5154e2f35c57b46817c36ea669c6a9d0f5797
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493537"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Criar um aplicativo de vários contêineres com o Docker Compose

Neste tutorial, você aprenderá a gerenciar mais de um contêiner e a se comunicar entre eles ao usar o Docker Compose no Visual Studio para Mac.

## <a name="prerequisites"></a>Pré-requisitos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio para Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Criar um Aplicativo Web ASP.NET Core e adicionar suporte ao Docker

1. Crie uma nova solução acessando **Arquivo > Nova Solução**.
1. Em **Web e Console > aplicativo,** escolha o modelo de **aplicativo Web** : ![ criar um novo aplicativo ASP.net](media/docker-quickstart-1.png)
1. Selecione a estrutura de destino. Neste exemplo, usaremos o .NET Core 3,1: ![ definir estrutura de destino](media/docker-quickstart-2.png)
1. Insira os detalhes do projeto, como o Nome do Projeto ( _DockerDemoFrontEnd_ neste exemplo) e o Nome da Solução ( _DockerDemo_ ). O projeto criado contém todos os princípios necessários para compilar e executar um site do ASP.NET Core.
1. Na janela da solução, clique com o botão direito do mouse no projeto DockerDemoFrontEnd e selecione **adicionar > adicionar suporte ao Docker** : ![ Adicionar suporte do Docker](media/docker-quickstart-3.png)

O Visual Studio para Mac vai adicionar automaticamente um novo projeto à sua solução denominado **docker-compose** e um **Dockerfile** ao seu projeto existente.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Criar uma API Web ASP.NET Core e adicionar suporte ao Docker

Em seguida, criaremos um segundo projeto que atuará como nossa API de back-end. O modelo **API do .NET Core** inclui um controlador que nos permite lidar com solicitações RESTful.

1. Adicione um novo projeto à solução existente clicando com botão direito na solução e escolhendo **Adicionar > Adicionar Novo Projeto**.
1. Em **Web e Console > aplicativo,** escolha o modelo de **API** .
1. Selecione a estrutura de destino. Neste exemplo, usaremos o .NET Core 3,1.
1. Insira os detalhes do projeto, como nome do projeto ( _MyWebAPI_ neste exemplo).
1. Depois de criado, vá para a janela da solução e clique com o botão direito do mouse no projeto MyWebAPI e selecione **adicionar > adicionar suporte ao Docker**.

O arquivo **docker-compose.yml** no projeto **docker-compose** será automaticamente atualizado para incluir o projeto de API com o projeto de aplicativo Web existente. Quando compilamos e executamos o projeto **docker-compose** , cada um desses projetos é implantado em um contêiner do Docker separado.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integrar os dois contêineres

Agora temos dois projetos ASP.NET em nossa solução e ambos estão configurados com suporte ao Docker. Em seguida, precisamos adicionar algum código!

1. No `DockerDemoFrontEnd` projeto, abra o arquivo *pages/index. cshtml. cs* e substitua o `OnGet` método pelo código a seguir:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > No código de produção, você não deve descartar `HttpClient` após cada solicitação. Para obter as práticas recomendadas, consulte [usar HttpClientFactory para implementar solicitações HTTP resilientes](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. No arquivo *Index.cshtml* , adicione uma linha para exibir `ViewData["Message"]` de modo que o arquivo se pareça com o seguinte código:

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```
  
1. Nos projetos de front-end e da API Web, comente a chamada para [Microsoft. AspNetCore. Builder. HttpsPolicyBuilderExtensions. UseHttpsRedirection](/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) no `Configure` método em *Startup.cs* , pois esse código de exemplo usa http, não HTTPS, para chamar a API da Web.

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. Defina o projeto `docker-compose` como o projeto de inicialização e vá para **Executar > Iniciar Depuração**. Se tudo estiver configurado corretamente, você verá a mensagem "Olá do webfrontend e webapi (com o valor 1).":

![Execução da solução de vários contêineres do Docker](media/docker-multicontainer-debug.png)