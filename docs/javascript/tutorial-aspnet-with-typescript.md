---
title: Criar um aplicativo ASP.NET Core com TypeScript
description: Neste tutorial, você cria um aplicativo usando ASP.NET Core e TypeScript
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 40011b035afdf4a04eb760d13c001e39d9c578c4
ms.sourcegitcommit: 91a054beb6b3a16ed5140f9f829239ec31bbbec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75810577"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Tutorial: criar um aplicativo ASP.NET Core com TypeScript no Visual Studio

Neste tutorial para o desenvolvimento do Visual Studio ASP.NET Core e TypeScript, você cria um aplicativo Web simples, adiciona um código TypeScript e, em seguida, executa o aplicativo. 

::: moniker range="vs-2017"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads) para instalá-lo gratuitamente.

::: moniker-end

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Criar um projeto ASP.NET Core
> * Adicionar o pacote NuGet para o suporte do TypeScript
> * Adicionar um código TypeScript
> * Executar o aplicativo

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

* Você deve ter o Visual Studio instalado e a carga de trabalho de desenvolvimento da Web do ASP.NET.

    ::: moniker range=">=vs-2019"
    Se você ainda não instalou o Visual Studio 2019, acesse a página  [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalá-lo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se você ainda não instalou o Visual Studio 2017, acesse a página  [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalá-lo gratuitamente.
    ::: moniker-end

    Caso precise instalar a carga de trabalho, mas já tiver o Visual Studio, acesse **Ferramentas** > **Obter Ferramentas e Funcionalidades...** , que abre o Instalador do Visual Studio. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Criar um novo projeto ASP.NET Core MVC

O Visual Studio gerencia arquivos de um único aplicativo em um *projeto*. O projeto inclui os arquivos de configuração, recursos e código-fonte.

Neste tutorial, você começa com um projeto simples contendo código para um aplicativo ASP.NET Core MVC.

1. {1&gt;Abra o Visual Studio.&lt;1}

1. Crie um novo projeto.

    ::: moniker range=">=vs-2019"
    Pressione **Esc** para fechar a janela de início. Digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **ASP.NET**e escolha **ASP.NET Core aplicativo Web- C#** . Na caixa de diálogo que aparece, escolha **Criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**. No painel esquerdo da caixa de diálogo **novo projeto** , expanda **Visual C#** e, em seguida, escolha **.NET Core**. No painel central, escolha **ASP.NET Core aplicativo Web C#-** e escolha **OK**.
    ::: moniker-end
    Se você não vir o modelo de projeto de **aplicativo web ASP.NET Core** , deverá adicionar a ASP.net e a carga de trabalho de **desenvolvimento Web** . Confira instruções detalhadas nos [Pré-requisitos](#prerequisites).

1. Depois de escolher **criar**, selecione **aplicativo Web (Model-View-Controller)** na caixa de diálogo e, em seguida, escolha **criar**.

   ![Escolher o modelo MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    O Visual Studio cria a solução e abre o projeto no painel direito.

## <a name="add-some-code"></a>Adicionar código

1. Na Gerenciador de Soluções (painel direito). Clique com o botão direito do mouse no nó do projeto e escolha **gerenciar pacotes NuGet**. Na guia **procurar** , procure **Microsoft. TypeScript. MSBuild**e clique em **instalar** à direita para instalar o pacote.

   ![Adicionar pacote NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   O Visual Studio adiciona o pacote NuGet sob o nó **dependências** em Gerenciador de soluções.

   > [!NOTE]
   > Este tutorial requer o pacote NuGet. Como alternativa, em seus próprios aplicativos, talvez você queira usar o [pacote NPM TypeScript](https://www.npmjs.com/package/typescript).

1. Em Gerenciador de Soluções, clique com o botão direito do mouse no nó do projeto e escolha **adicionar > nova pasta**. Use os *scripts* de nome para a nova pasta.

1. Clique com o botão direito do mouse na pasta *scripts* e escolha **Adicionar > novo item**. Escolha o **arquivo de configuração JSON do TypeScript**e clique em **Adicionar**.

   O Visual Studio adiciona o arquivo *tsconfig. JSON* à pasta *scripts* . Você pode usar esse arquivo para [Configurar opções](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) para o compilador TypeScript.

1. Abra *tsconfig. JSON* e substitua o código padrão pelo código a seguir:

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   A opção *outDir* especifica a pasta de saída para o plano de arquivos JavaScript que são transcompilados pelo compilador TypeScript.

   Essa configuração fornece uma introdução básica ao uso do TypeScript. Em outros cenários, por exemplo, ao usar o [Gulp ou o webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), talvez você queira um local intermediário diferente para os arquivos JavaScript transcompilados, dependendo de suas ferramentas e preferências de configuração, em vez de *.. /wwwroot/js*.

1. Clique com o botão direito do mouse na pasta *scripts* e escolha **Adicionar > novo item**. Escolha o **arquivo TypeScript**, digite o nome *app. TS* para o nome de arquivo e clique em **Adicionar**.

   O Visual Studio adiciona *app. TS* à pasta *scripts* .

1. Abra *app. TS* e adicione o código TypeScript a seguir.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    O Visual Studio fornece suporte IntelliSense para seu código TypeScript.

    Para testar isso, remova `.lastName` da função `greeter`, em seguida, digite novamente o "." e você verá o IntelliSense.

    ![Exibir IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Selecione `lastName` para adicionar o sobrenome de volta ao código.

1. Abra a pasta *views/Home* e, em seguida, abra *index. html*.

1. Adicione o código HTML a seguir ao final do arquivo.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Abra os *modos de exibição/pasta compartilhada* e, em seguida, abra *_Layout. cshtml*.

1. Adicione a seguinte referência de script antes da chamada para `@RenderSection("Scripts", required: false)`:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Compilar o aplicativo

1. Escolha **compilar > Compilar solução**.

   Embora o aplicativo seja criado automaticamente quando você o executa, queremos dar uma olhada em algo que acontece durante o processo de compilação.

1. Abra a pasta *wwwroot/js* e você encontrará dois arquivos novos, *app. js* e o arquivo de mapa de origem, *app. js. map*. Esses arquivos são gerados pelo compilador TypeScript.

   Os arquivos de mapa de origem são necessários para depuração.

## <a name="run-the-application"></a>Executar o aplicativo

1. Pressione **F5** (**Depurar** > **Iniciar Depuração**) para executar o aplicativo.

    O aplicativo é aberto em um navegador.

    Na janela do navegador, você verá o título de **boas-vindas** e o botão **clicar em mim** .

    ![ASP.NET Core com TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Clique no botão para exibir a mensagem que especificamos no arquivo TypeScript.

## <a name="debug-the-application"></a>Depurar o aplicativo

1. Defina um ponto de interrupção na função `greeter` em `app.ts` clicando na margem esquerda no editor de códigos.

    ![Definir um ponto de interrupção](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Pressione **F5** para executar o aplicativo.

   Talvez seja necessário responder a uma mensagem para habilitar a depuração de script.

   O aplicativo pausa no ponto de interrupção. Agora, você pode inspecionar variáveis e usar os recursos do depurador.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Talvez você queira saber mais detalhes sobre como usar o TypeScript com ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core e TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
