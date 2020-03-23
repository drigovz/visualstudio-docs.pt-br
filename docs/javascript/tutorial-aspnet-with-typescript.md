---
title: Criar um aplicativo ASP.NET Core com o TypeScript
description: Neste tutorial, você cria um aplicativo usando ASP.NET Core e TypeScript
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988558"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Tutorial: Crie um aplicativo ASP.NET Core com TypeScript no Visual Studio

Neste tutorial para desenvolvimento do Visual Studio ASP.NET Core e TypeScript, você cria um aplicativo web simples, adiciona algum código TypeScript e, em seguida, executa o aplicativo. 

::: moniker range="vs-2017"

Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do Visual Studio para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/downloads) do Visual Studio para instalá-lo gratuitamente.

::: moniker-end

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Crie um projeto ASP.NET Core
> * Adicione o pacote NuGet para suporte ao TypeScript
> * Adicione algum código TypeScript
> * Executar o aplicativo
> * Adicione uma biblioteca de terceiros usando npm

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter o Visual Studio instalado e a carga de trabalho de desenvolvimento web ASP.NET.

    ::: moniker range=">=vs-2019"
    Se você ainda não instalou o Visual Studio 2019, acesse a página [de downloads](https://visualstudio.microsoft.com/downloads/) do Visual Studio para instalá-lo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se você ainda não instalou o Visual Studio 2017, acesse a página [de downloads](https://visualstudio.microsoft.com/downloads/) do Visual Studio para instalá-lo gratuitamente.
    ::: moniker-end

    Se você precisa instalar a carga de trabalho, mas já tem o Visual Studio, vá para **Ferramentas** > **Obter Ferramentas e Recursos...**, que abre o Visual Studio Installer. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Crie um novo projeto ASP.NET Core MVC

O Visual Studio gerencia arquivos de um único aplicativo em um *projeto*. O projeto inclui os arquivos de configuração, recursos e código-fonte.

>[!NOTE]
> Para começar com um projeto ASP.NET Core vazio e adicionar um frontend TypeScript, consulte [ASP.NET Core com TypeScript.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

Neste tutorial, você começa com um projeto simples contendo código para um aplicativo MVC ASP.NET.

1. Abra o Visual Studio.

1. Criar um novo projeto.

    ::: moniker range=">=vs-2019"
    Se a janela inicial não estiver aberta, escolha**Janela inicial de** **arquivo** > . Na janela inicial, escolha **Criar um novo projeto**. Na lista de despontados do idioma, escolha **C#**. Na caixa de pesquisa, digite **ASP.NET**e escolha **ASP.NET Aplicativo Web Central**. Escolha **a seguir**.

    Digite um nome para o projeto e escolha **Criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na barra de menu superior, escolha **Arquivo** > **Novo** > **Projeto**. No painel esquerdo da caixa de diálogo **Novo Projeto,** expanda **o Visual C#** e escolha **.NET Core**. No painel do meio, escolha **ASP.NET Aplicativo Web Central - C#**, em seguida, escolha **OK**.
    ::: moniker-end
    Se você não ver o modelo de projeto **ASP.NET Do Aplicativo Web,** você deve adicionar a carga de trabalho **de desenvolvimento ASP.NET e web.** Confira instruções detalhadas nos [Pré-requisitos](#prerequisites).

1. Na caixa de diálogo que aparece, selecione **'Aplicativo da Web(Model-View-Controller)** na caixa de diálogo e escolha **Criar** (ou **OK**).

   ![Escolha o modelo MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    O Visual Studio cria a solução e abre o projeto no painel direito.

## <a name="add-some-code"></a>Adicionar código

1. No Solution Explorer (painel direito). clique com o botão direito do mouse no nó do projeto e escolha **Gerenciar pacotes NuGet**. Na guia **Procurar,** procure por **Microsoft.TypeScript.MSBuild**e clique em **Instalar** no direito de instalar o pacote.

   ![Adicionar pacote NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   O Visual Studio adiciona o pacote NuGet o nó **Dependencies** no Solution Explorer.

   > [!NOTE]
   > Este tutorial requer o pacote NuGet. Alternativamente, em seus próprios aplicativos, você pode querer usar o [pacote npm TypeScript](https://www.npmjs.com/package/typescript).

1. No Solution Explorer, clique com o botão direito do mouse no nó do projeto e escolha **Adicionar > Nova pasta**. Use os *scripts de* nome para a nova pasta.

1. Clique com o botão direito do mouse na pasta *scripts* e escolha **Adicionar > Novo Item**. Escolha o **arquivo de configuração TypeScript JSON**e clique em **Adicionar**.

   O Visual Studio adiciona o arquivo *tsconfig.json* à pasta *scripts.* Você pode usar este arquivo para [configurar opções](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) para o compilador TypeScript.

1. Abra *tsconfig.json* e substitua o código padrão pelo seguinte código:

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

   A opção *outDir* especifica a pasta de saída para os arquivos JavaScript do plano que são transcompilados pelo compilador TypeScript.

   Esta configuração fornece uma introdução básica ao uso do TypeScript. Em outros cenários, por exemplo, ao usar [gulp ou webpack,](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)você pode querer um local intermediário diferente para os arquivos JavaScript transcompilados, dependendo de suas ferramentas e preferências de configuração, em vez de *.. /wwwroot/js*.

1. Clique com o botão direito do mouse na pasta *scripts* e escolha **Adicionar > Novo Item**. Escolha o **Arquivo TypeScript,** digite o *nome app.ts* para o nome do arquivo e clique **em Adicionar**.

   O Visual Studio adiciona *app.ts* à pasta *scripts.*

1. Abra *app.ts* e adicione o seguinte código TypeScript.

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

    O Visual Studio fornece suporte ao IntelliSense para seu código TypeScript.

    Para testar isso, `.lastName` `greeter` remova da função, depois redigite o ".", e você verá o IntelliSense.

    ![Ver IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Selecione `lastName` para adicionar o sobrenome de volta ao código.

1. Abra a *pasta 'Visualizações/ Home'* e, em seguida, abra *o index.html*.

1. Adicione o seguinte código HTML ao final do arquivo.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Abra a *pasta 'Visualizações/ Compartilhada',* e depois abra *_Layout.cshtml*.

1. Adicione a seguinte referência de `@RenderSection("Scripts", required: false)`script antes da chamada para:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Compilar o aplicativo

1. Escolha **construir > construir solução**.

   Embora o aplicativo seja construído automaticamente quando você executá-lo, queremos dar uma olhada em algo que acontece durante o processo de compilação.

1. Abra a pasta *wwwroot/js,* e você encontrará dois novos arquivos, *app.js* e o arquivo de mapa de origem, *app.js.map*. Esses arquivos são gerados pelo compilador TypeScript.

   Os arquivos do mapa de origem são necessários para depuração.

## <a name="run-the-application"></a>Executar o aplicativo

1. Pressione **F5** (**Depurar** > **Iniciar Depuração**) para executar o aplicativo.

    O aplicativo é aberto em um navegador.

    Na janela do navegador, você verá o título **De boas-vindas** e o botão **Clique em Mim.**

    ![núcleo de ASP.NET com TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Clique no botão para exibir a mensagem especificada no arquivo TypeScript.

## <a name="debug-the-application"></a>Depurar o aplicativo

1. Defina um ponto `greeter` de `app.ts` ruptura na função clicando na margem esquerda no editor de código.

    ![Definir um ponto de interrupção](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Pressione **F5** para executar o aplicativo.

   Você pode precisar responder a uma mensagem para ativar a depuração de script.

   O aplicativo faz uma pausa no ponto de ruptura. Agora, você pode inspecionar variáveis e usar recursos de depurador.

## <a name="add-typescript-support-for-a-third-party-library"></a>Adicionar suporte ao TypeScript para uma biblioteca de terceiros

1. Siga as instruções no gerenciamento `package.json` de [pacotes npm](../javascript/npm-package-management.md#aspnet-core-projects) para adicionar um arquivo ao seu projeto. Isso adiciona suporte npm ao seu projeto.

   >[!NOTE]
   > Para ASP.NET projetos Core, você também pode usar [o Library Manager](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) ou o fio em vez de npm para instalar arquivos JavaScript e CSS do lado do cliente.

1. Neste exemplo, adicione um arquivo de definição TypeScript para jQuery ao seu projeto. Inclua o seguinte no seu arquivo *package.json.*

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Isso adiciona suporte ao TypeScript para jQuery. A biblioteca jQuery em si já está incluída no modelo de projeto MVC (veja em wwwroot/lib no Solution Explorer). Se você estiver usando um modelo diferente, talvez seja necessário incluir o pacote jquery npm também.

1. Se o pacote no Solution Explorer não estiver instalado, clique com o botão direito do mouse no nó npm e escolha **Restaurar pacotes**.

   >[!NOTE]
   > Em alguns cenários, o Solution Explorer pode indicar que um pacote npm está fora de sincronia com *o package.json* devido a um problema conhecido descrito [aqui](https://github.com/aspnet/Tooling/issues/479). Por exemplo, o pacote pode aparecer como não instalado quando está instalado. Na maioria dos casos, você pode atualizar o Solution Explorer excluindo *o package.json*, reiniciando o Visual Studio e adicionando o arquivo *package.json* como descrito anteriormente neste artigo.

1. No Solution Explorer, clique com o botão direito do mouse na pasta scripts e escolha **Adicionar** > **novo item**.

1. Escolha **TypeScript File,** type *library.ts*e escolha **Adicionar**.

1. Em *library.ts,* adicione o seguinte código.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Para simplificar, este código exibe uma mensagem usando jQuery e um alerta.

   Com definições de tipo TypeScript para jQuery adicionadas, você recebe suporte do IntelliSense em objetos jQuery quando digita um "." seguindo um objeto jQuery, como mostrado aqui.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. Em _Layout.cshtml, atualize as `library.js`referências de script para incluir .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Em Index.cshtml, adicione o HTML a seguir ao final do arquivo.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Pressione **F5** (**Depurar** > **Iniciar Depuração**) para executar o aplicativo.

    O aplicativo é aberto no navegador.

    Clique em **OK** no alerta para ver a página atualizada para a **versão jQuery é: 3.3.1!!**.

    ![exemplo de jquery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Próximas etapas

Você pode querer saber mais detalhes sobre como usar o TypeScript com ASP.NET Core.

> [!div class="nextstepaction"]
> [núcleo de ASP.NET e script de digitação](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
