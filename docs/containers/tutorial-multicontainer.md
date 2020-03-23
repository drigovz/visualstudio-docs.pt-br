---
title: Tutorial multicontainer usando Docker Compose & ASP.NET Core
author: ghogen
description: Aprenda a usar vários contêineres com o Docker Compose
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027329"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Tutorial: Crie um aplicativo multi-contêiner com o Docker Compose

Neste tutorial, você aprenderá a gerenciar mais de um contêiner e se comunicar entre eles ao usar ferramentas de contêiner no Visual Studio.  Gerenciar vários contêineres requer *orquestração de contêineres* e requer um orquestrador como Docker Compose, Kubernetes ou Service Fabric. Aqui, vamos usar Docker Compose. O Docker Compose é ótimo para depuração e testes locais no decorrer do ciclo de desenvolvimento.

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) com a carga **de trabalho de desenvolvimento web,** **azure Tools** ou a carga de trabalho de desenvolvimento **multiplataforma .NET Core** instalada
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) com **Desenvolvimento para a Web**, a carga de trabalho de **Ferramentas do Azure** e/ou **Desenvolvimento multiplataforma do .NET Core** instalados
* [Ferramentas de desenvolvimento do .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) para o desenvolvimento com .NET Core 2.2
* [.NET Core 3 Ferramentas de desenvolvimento](https://dotnet.microsoft.com/download/dotnet-core/3.1) para desenvolvimento com .NET Core 3.1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Criar um projeto de Aplicativo Web

No Visual Studio, crie um projeto `WebFrontEnd`ASP.NET Do Core Web **Application,** chamado . Selecione **o Aplicativo web** para criar um aplicativo web com páginas de Navalha. 
  
::: moniker range="vs-2017"

Não selecione **Habilitar Suporte ao Docker**. Você adicionará suporte ao Docker mais tarde.

![Captura de tela da criação do projeto web](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Captura de tela da criação do projeto web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Não selecione **Habilitar Suporte ao Docker**. Você adicionará suporte ao Docker mais tarde.

![Captura de tela da criação do projeto web](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Crie um projeto de API web

Adicione um projeto à mesma solução e chame-o *de MyWebAPI*. Selecione **a API** como o tipo de projeto e limpe a caixa de seleção para **Configurar para HTTPS**. Neste design, estamos usando apenas SSL para comunicação com o cliente, não para comunicação entre contêineres na mesma aplicação web. Só `WebFrontEnd` precisa de HTTPS e o código nos exemplos assume que você limpou essa caixa de seleção.

::: moniker range="vs-2017"
   ![Captura de tela da criação do projeto de API da Web](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Captura de tela da criação do projeto de API da Web](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Adicionar código para chamar a API da Web

1. No `WebFrontEnd` projeto, abra o *arquivo* Index.cshtml.cs `OnGet` e substitua o método pelo seguinte código.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > No código do mundo real, `HttpClient` você não deve se desfazer depois de cada pedido. Para obter práticas recomendadas, consulte [Use HttpClientFactory para implementar solicitações HTTP resilientes](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Para .NET Core 3.1 no Visual Studio 2019 ou posterior, o modelo de API da Web usa uma API WeatherForecast, então não comente essa linha e comente a linha para ASP.NET 2.x.

1. No arquivo *Index.cshtml*, adicione uma linha para exibir `ViewData["Message"]` de modo que o arquivo se pareça com o seguinte código:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (somente ASP.NET 2.x) Agora, no projeto de API da Web, adicione código ao controlador Valores para personalizar a mensagem retornada pela API para a chamada adicionada do *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    Com o .NET Core 3.1, você não precisa disso, porque você pode usar a API WeatherForecast que já está lá. No entanto, você precisa <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> comentar `Configure` a chamada para o método em *Startup.cs,* porque este código usa HTTP, não HTTPS, para chamar a API da Web.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. No `WebFrontEnd` projeto, escolha **Adicionar > suporte ao orquestrador de contêineres**. A **caixa de diálogo Opções de suporte** do Docker é exibida.

1. Escolha **Docker Compose**.

1. Escolha seu Sistema Operacional Alvo, por exemplo, Linux.

   ![Captura de tela de escolher o Sistema Operacional Alvo](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   O Visual Studio cria um arquivo *docker-compose.yml* e um arquivo *.dockerignore* no nó **de composição do docker** na solução, e esse projeto é mostrado na fonte boldface, o que mostra que é o projeto de inicialização.

   ![Captura de tela do Solution Explorer com projeto de composição de docker adicionado](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   O *docker-compose.yml* aparece da seguinte forma:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   O arquivo *.dockerignore* contém tipos de arquivo e extensões que você não deseja que o Docker inclua no contêiner. Esses arquivos são geralmente associados ao ambiente de desenvolvimento e controle de origem, não parte do aplicativo ou serviço que você está desenvolvendo.

   Veja a seção Ferramentas de **contêiner** do painel de saída para obter detalhes sobre os comandos que estão sendo executados.  Você pode ver que a ferramenta de linha de comando docker-compose é usada para configurar e criar os contêineres de tempo de execução.

1. No projeto De PiO Web, clique novamente com o botão direito do mouse no nó do projeto e escolha **Adicionar** > **suporte ao Orquestrador de contêineres**. Escolha **Docker Compose**e selecione o mesmo sistema operacional de destino.  

    > [!NOTE]
    > Nesta etapa, o Visual Studio oferecerá a criação de um Arquivo Docker. Se você fizer isso em um projeto que já tem suporte ao Docker, você será solicitado se deseja substituir o Arquivo Docker existente. Se você fez alterações no seu Arquivo Docker que você deseja manter, escolha não.

    Visual Studio faz algumas alterações no seu docker compor arquivo YML. Agora ambos os serviços estão incluídos.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Execute o site localmente agora (F5 ou Ctrl+F5) para verificar se ele funciona como esperado. Se tudo estiver configurado corretamente com a versão .NET Core 2.x, você verá a mensagem "Olá do webfrontend e webapi (com valor 1)."  Com .NET Core 3, você vê os dados da previsão do tempo.

   O primeiro projeto que você usa quando adiciona orquestração de contêineres é configurado para ser lançado quando você executar ou depurar. Você pode configurar a ação de lançamento no **Project Properties** para o projeto de composição de docker.  No nó do projeto de composição de docker, clique com o botão direito do mouse para abrir o menu de contexto e, em seguida, escolha **Propriedades**ou use Alt+Enter.  A captura de tela a seguir mostra as propriedades que você gostaria para a solução usada aqui.  Por exemplo, você pode alterar a página que é carregada personalizando a propriedade **URL do Serviço.**

   ![Captura de tela das propriedades do projeto de composição do docker](media/tutorial-multicontainer/launch-action.png)

   Aqui está o que você vê quando lançado (a versão .NET Core 2.x):

   ![Captura de tela do aplicativo web em execução](media/tutorial-multicontainer/webfrontend.png)

   O aplicativo web para .NET 3.1 mostra os dados meteorológicos no formato JSON.

## <a name="next-steps"></a>Próximas etapas

Veja as opções para implantar seus [contêineres no Azure](/azure/containers).

## <a name="see-also"></a>Confira também
  
[Docker Compose](https://docs.docker.com/compose/)  
[Ferramentas de contêineres](/visualstudio/containers/)
