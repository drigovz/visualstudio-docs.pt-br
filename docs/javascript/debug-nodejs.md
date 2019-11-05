---
title: Depurar um aplicativo JavaScript ou TypeScript
description: O Visual Studio fornece suporte para depuração de aplicativos JavaScript e TypeScript no Visual Studio
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 5fbaa25146c9e06f3a12b90ab2d6ae124fbbd189
ms.sourcegitcommit: ee9c55616a22addc89cf1cf1942bf371d73e2e11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73618098"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Depurar um aplicativo JavaScript ou TypeScript no Visual Studio

Depure o código JavaScript e TypeScript usando o Visual Studio. Defina e atinja pontos de interrupção, anexe o depurador, inspecione variáveis, exiba a pilha de chamadas e use outras funcionalidades de depuração.

> [!TIP]
> Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalá-lo gratuitamente. Dependendo do tipo de desenvolvimento de aplicativo que você estiver fazendo, talvez você precise instalar a **carga de trabalho de desenvolvimento em Node.js** com o Visual Studio.

## <a name="debug-server-side-script"></a>Depurar um script do servidor

1. Com o projeto aberto no Visual Studio, abra um arquivo JavaScript do servidor (como *server.js*), clique na medianiz da medianiz esquerda para definir um ponto de interrupção:

    ![Definir um ponto de interrupção](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não.

1. Para executar o aplicativo, pressione **F5** (**Depurar** > **Iniciar Depuração**).

    O depurador pausa no ponto de interrupção definido (a instrução atual é marcada em amarelo). Agora, você pode inspecionar o estado do aplicativo passando o mouse sobre as variáveis que estão no escopo, usando as janelas do depurador, como **Locais** e **Inspecionar**.

1. Pressione **F5** para continuar o aplicativo.

1. Caso deseje usar as Ferramentas para Desenvolvedores do Chrome ou as Ferramentas F12, pressione **F12**. Você pode usar essas ferramentas para examinar o DOM e interagir com o aplicativo usando o Console do JavaScript.

## <a name="debug-client-side-script"></a>Depurar um script do lado do cliente

::: moniker range=">=vs-2019"
O Visual Studio fornece suporte de depuração do lado do cliente somente para Chrome e Microsoft Edge (Chromium). Em alguns cenários, o depurador atinge automaticamente os pontos de interrupção no código JavaScript e TypeScript e em scripts inseridos em arquivos HTML. Para depurar o script do lado do cliente em aplicativos ASP.NET, consulte a postagem do blog [Depurar JavaScript no Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) e esta [postagem para o Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome).
::: moniker-end
::: moniker range="vs-2017"
O Visual Studio fornece suporte de depuração do lado do cliente somente para Chrome e Internet Explorer. Em alguns cenários, o depurador atinge automaticamente os pontos de interrupção no código JavaScript e TypeScript e em scripts inseridos em arquivos HTML. Para depurar o script do lado do cliente em aplicativos ASP.NET, consulte a postagem do blog [depuração do lado do cliente de projetos do ASP.net no Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Se a fonte for minificada ou criada por um transcompilador como o TypeScript ou o Babel, o uso de [mapas de origem](#generate_sourcemaps) será necessário para proporcionar a melhor experiência de depuração. Sem mapas de origem, você ainda poderá anexar o depurador a um script do lado do cliente em execução. No entanto, você só poderá definir e atingir pontos de interrupção no arquivo minificado ou transcompilado, não no arquivo de origem original. Por exemplo, em um aplicativo Vue.js, o script minificado é passado como uma cadeia de caracteres para uma instrução `eval`, e não há nenhuma maneira de executar esse código em etapas com eficiência usando o depurador do Visual Studio, a menos que você use mapas de origem. Em cenários de depuração complexos, você pode usar o Chrome Ferramentas para Desenvolvedores ou as ferramentas F12 para o Microsoft Edge.

### <a name="attach-the-debugger-to-client-side-script"></a>Anexar o depurador ao script do lado do cliente

Para anexar o depurador do Visual Studio e clicar em pontos de interrupção no código do lado do cliente, o depurador precisa de ajuda para identificar o processo correto. Esta é uma maneira de permitir isso.

::: moniker range=">=vs-2019"
Para este cenário, use o Microsoft Edge (Chromium), atualmente chamado de **Microsoft Edge beta** no IDE ou Chrome.
::: moniker-end
::: moniker range="vs-2017"
Para este cenário, use o Chrome.
::: moniker-end

1. Feche todas as janelas do navegador de destino.

   Outras instâncias do navegador podem impedir que o navegador seja aberto com a depuração habilitada. (As extensões do navegador podem estar em execução e impedindo o modo de depuração completa, portanto, talvez seja necessário abrir o Gerenciador de tarefas para localizar instâncias inesperadas do Chrome.)

   ::: moniker range=">=vs-2019"
   Para o Microsoft Edge (Chromium), também Desligue todas as instâncias do Chrome. Como ambos os navegadores usam a base de código Chromium, isso fornece os melhores resultados.
   ::: moniker-end

2. Abra o comando **Executar** do botão **Iniciar** do Windows (clique com o botão direito do mouse e escolha **Executar**) e digite o seguinte comando:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker range=">=vs-2019"
    ou, `msedge --remote-debugging-port=9222`
    ::: moniker-end

    Isso inicia o navegador com a depuração habilitada.

    ::: moniker range=">=vs-2019"

    > [!TIP]
    > A partir do Visual Studio 2019, você pode definir o sinalizador `--remote-debugging-port` na inicialização do navegador selecionando **procurar com...** > na barra de ferramentas **depurar** , escolhendo **Adicionar**e, em seguida, definindo o sinalizador no campo **argumentos** . Use um nome amigável diferente para o navegador, como **borda com depuração** ou **Chrome com depuração**. Para obter detalhes, confira [Notas sobre a versão](/visualstudio/releases/2019/release-notes-v16.2).

    ![Definir o navegador para abrir com a depuração habilitada](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    ::: moniker-end

    O aplicativo ainda não está em execução e, portanto, você obtém uma página vazia do navegador.

3. Alterne para o Visual Studio e defina um ponto de interrupção no código-fonte, que pode ser um arquivo JavaScript, um arquivo TypeScript ou um arquivo JSX. (Defina o ponto de interrupção em uma linha de código que permite pontos de interrupção, como uma instrução de retorno ou uma declaração var.)

    ![Definir um ponto de interrupção](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Para localizar o código específico em um arquivo transcompilado, use **Ctrl**+**F** (**editar** > **Localizar e substituir** > **localização rápida**).

    Para o código do lado do cliente, para atingir um ponto de interrupção em um arquivo TypeScript ou JSX, o arquivo geralmente requer o uso de [sourcemaps](#generate_sourcemaps). Um sourcemap deve ser configurado corretamente para dar suporte à depuração no Visual Studio.

4. (Somente webpack) Siga as instruções descritas em [gerar sourcemaps](#generate_sourcemaps).

5. Selecione o navegador de destino como o destino de depuração no Visual Studio e pressione **Ctrl**+**F5** (**depurar** > **Iniciar sem depuração**) para executar o aplicativo no navegador.

    O aplicativo será aberto em uma nova guia do navegador.

6. Escolha **Depurar** > **Anexar ao Processo**.

7. Na caixa de diálogo **anexar ao processo** , obtenha uma lista filtrada de instâncias do navegador às quais você pode anexar.

    ::: moniker range=">=vs-2019"
    No Visual Studio 2019, escolha o navegador de destino, **JavaScript (Chrome)** ou **JavaScript correto (Microsoft Edge-Chromium)** no campo **anexar a** , digite **Chrome** ou **Edge** na caixa de filtro para filtrar os resultados da pesquisa. Se você tiver criado uma configuração de navegador com um nome amigável, escolha isso em vez disso.
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, escolha **código WebKit** no campo **anexar a** , digite **Chrome** na caixa de filtro para filtrar os resultados da pesquisa.
    ::: moniker-end

8. Selecione o processo de navegador com a porta de host correta (localhost neste exemplo) e selecione **anexar**.

    A porta (por exemplo, 1337) também pode aparecer no campo **título** para ajudá-lo a selecionar a instância correta do navegador.

    ::: moniker range=">=vs-2019"
    O exemplo a seguir mostra como isso se parece com o navegador Microsoft Edge (Chromium).

    ![Anexar ao processo](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Anexar ao processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Você sabe que o depurador foi anexado corretamente quando o Explorador do DOM e o Console do JavaScript são abertos no Visual Studio. Essas ferramentas de depuração são semelhantes às Ferramentas para Desenvolvedores do Chrome e às Ferramentas F12 do Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Se o depurador não anexar e você vir a mensagem "falha ao iniciar o adaptador de depuração" ou "não é possível anexar ao processo. Uma operação não é válida no estado atual. ", use o Gerenciador de tarefas do Windows para fechar todas as instâncias do navegador de destino antes de iniciar o navegador no modo de depuração. As extensões de navegador podem estar em execução e impedindo o modo de depuração completa.

9. Como o código com o ponto de interrupção pode já ter sido executado, atualize a página do navegador. Se necessário, tome medidas para fazer com que o código com o ponto de interrupção seja executado.

    Enquanto estiver em pausa no depurador, você pode examinar o estado do aplicativo passando o mouse sobre as variáveis e usando as janelas do depurador. Você pode avançar o depurador percorrendo o código (**F5**, **F10** e **F11**).

    Você pode atingir o ponto de interrupção no arquivo *. js* transcompilado ou no arquivo de origem, dependendo de quais etapas você seguiu anteriormente, junto com o seu ambiente e o estado do navegador. De qualquer forma, você pode percorrer o código e examinar as variáveis.

   * Se você precisar dividir o código em um arquivo de origem TypeScript ou JSX e não puder fazê-lo, use **anexar ao processo** conforme descrito nas etapas anteriores para anexar o depurador. Verifique se o seu ambiente está configurado corretamente:

      * Você fechou todas as instâncias de navegador, incluindo as extensões Chrome (usando o Gerenciador de tarefas), para que você possa executar o navegador no modo de depuração. Certifique-se de iniciar o navegador no modo de depuração.

      * Verifique se o arquivo sourcemap inclui uma referência ao seu arquivo de origem que não inclui prefixos sem suporte, como *webpack:///* , que impede que o depurador do Visual Studio localize o *app. TSX*. Por exemplo, essa referência pode ser corrigida para *./app.TSX*. Você pode fazer isso manualmente no arquivo sourcemap ou por meio de uma modificação de compilação personalizada.

       Como alternativa, se você precisar dividir o código em um arquivo de origem (por exemplo, * app. TSX) e não puder fazê-lo, tente usar a instrução `debugger;` no arquivo de origem ou definir pontos de interrupção no Chrome Ferramentas para Desenvolvedores (ou ferramentas F12 para o Microsoft Edge) em vez disso.

   * Se você precisar dividir o código em um arquivo JavaScript transcompilado (por exemplo, *app-Bundle. js*) e não puder fazê-lo, remova o arquivo sourcemap, filename. *js. map*.

     > [!TIP]
     > Após anexar ao processo pela primeira vez seguindo estas etapas, você pode rapidamente anexar novamente ao mesmo processo no Visual Studio 2017 escolhendo **Depurar** > **Reanexar ao Processo**.

## <a name="generate_sourcemaps"></a> Gerar mapas de origem para depuração

O Visual Studio tem a capacidade de usar e gerar mapas de origem em arquivos de origem JavaScript. Isso costuma ser necessário se a fonte é minificada ou criada por um transcompilador como o TypeScript ou o Babel. As opções disponíveis dependem do tipo de projeto.

* Por padrão, um projeto TypeScript no Visual Studio gera mapas de origem para você.

* Em um projeto JavaScript, é necessário gerar mapas de origem usando um empacotador como o webpack e um compilador como o compilador TypeScript (ou Babel), que pode ser adicionado ao projeto. Para o compilador TypeScript, também é necessário adicionar um arquivo *tsconfig.json*. Para obter um exemplo que mostra como fazer isso usando uma configuração básica de webpack, confira [Criar um aplicativo Node.js com o React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Caso não esteja familiarizado com mapas de origem, leia [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Introdução a mapas de origem JavaScript) antes de continuar. 

Para definir configurações avançadas para mapas de origem, use um *tsconfig.json* ou as configurações do projeto em um projeto TypeScript, mas não ambos.

Para habilitar a depuração usando o Visual Studio, você precisa certificar-se de que as referências ao arquivo de origem no sourcemap gerado estão corretas. Por exemplo, se você estiver usando o webpack, as referências no arquivo sourcemap incluem o prefixo *webpack:///* , que impede que o Visual Studio Localize um arquivo de origem TYPESCRIPT ou JSX. Especificamente, quando você corrige isso para fins de depuração, a referência ao arquivo de origem (como *app. TSX*) deve ser alterada de algo como *webpack:///./app.TSX* para algo como *./app.TSX*, que habilita a depuração (o o caminho é relativo ao arquivo de origem). O exemplo a seguir mostra como você pode corrigir o sourcemaps com o webpack, que é um dos pacotes mais comuns.

(Somente webpack) Se você estiver definindo o ponto de interrupção em um TypeScript de arquivo JSX (em vez de um arquivo JavaScript transcompilado), precisará atualizar sua configuração do webpack. Por exemplo, em *webpack-config. js*, talvez seja necessário substituir o seguinte código:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

com este código:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Essa é uma configuração somente de desenvolvimento para habilitar a depuração do código do lado do cliente no Visual Studio.

Para cenários complicados, as ferramentas de navegador (**F12**) podem funcionar melhor para depuração.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Configurar mapas de origem usando um arquivo tsconfig.json

Se você adicionar um arquivo *tsconfig.json* ao projeto, o Visual Studio tratará a raiz do diretório como um projeto TypeScript. Para adicionar o arquivo, no Gerenciador de Soluções, clique com o botão direito do mouse no projeto e, em seguida, escolha **Adicionar > Novo Item > Web > Scripts > Arquivo de Configuração JSON TypeScript**. Um arquivo *tsconfig.json* como o mostrado a seguir é adicionado ao projeto.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Opções do compilador para tsconfig.json

* **inlineSourceMap**: emitir um único arquivo com mapas de origem em vez de criar um mapa de origem separado para cada arquivo de origem.
* **inlineSources**: emitir a origem junto com os mapas de origem em um único arquivo; requer a definição de *inlineSourceMap* ou *sourceMap* .
* **mapRoot**: especifica o local em que o depurador deve localizar arquivos de mapa de origem ( *. map*) em vez do local padrão. Use esse sinalizador se os arquivos *.map* em tempo de execução precisarem estar em uma localização diferente dos arquivos *.js*. A localização especificada é inserida no mapa de origem para direcionar o depurador à localização dos arquivos *.map*.
* **sourceMap**: gera um arquivo *. map* correspondente.
* **sourceRoot**: especifica o local em que o depurador deve localizar arquivos TypeScript em vez dos locais de origem. Use esse sinalizador se as origens em tempo de execução precisarem estar em uma localização diferente da localização em tempo de design. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de origem.

Para obter mais detalhes sobre as opções do compilador, confira a página [Opções do compilador](https://www.typescriptlang.org/docs/handbook/compiler-options.html) no Manual do TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configurar mapas de origem usando configurações de projeto (projeto TypeScript)

Defina também as configurações de mapa de origem usando as propriedades do projeto clicando com o botão direito do mouse no projeto e, em seguida, escolhendo **Projeto > Propriedades > Build TypeScript > Depuração**.

Estas configurações do projeto estão disponíveis.

* **Gerar mapas de origem** (equivalente **a sourceMap** em *tsconfig. JSON*): gera o arquivo *. map* correspondente.
* **Especificar o diretório raiz dos mapas de origem** (equivalente a **mapRoot** em *tsconfig. JSON*): especifica o local onde o depurador deve encontrar arquivos de mapa em vez dos locais gerados. Use esse sinalizador se os arquivos *.map* em tempo de execução precisarem estar em uma localização diferente dos arquivos .js. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de mapa.
* **Especificar o diretório raiz de arquivos TypeScript** (equivalente a **sourceRoot** em *tsconfig. JSON*): especifica o local em que o depurador deve localizar arquivos TypeScript em vez de locais de origem. Use esse sinalizador se os arquivos de origem em tempo de execução precisarem estar em uma localização diferente da localização em tempo de design. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de origem.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Depurar JavaScript em arquivos dinâmicos usando o Razor (ASP.NET)

O Visual Studio fornece suporte de depuração somente para o Chrome e o Internet Explorer. Ele anexará automaticamente os pontos de interrupção ao JavaScript/TypeScript e aos scripts inseridos em arquivos HTML.

A depuração de arquivos gerados dinamicamente não é automática. Não é possível atingir automaticamente os pontos de interrupção em arquivos gerados com a sintaxe Razor (cshtml, vbhtml). Há duas abordagens que podem ser usadas para depurar esse tipo de arquivo:

* **Coloque a instrução `debugger;` onde você deseja interromper**: isso faz com que o script dinâmico interrompa a execução e inicie a depuração imediatamente enquanto está sendo criado.
* **Carregar a página e abrir o documento dinâmico no Visual Studio**: você precisará abrir o arquivo dinâmico durante a depuração, definir seu ponto de interrupção e atualizar a página para que esse método funcione. Dependendo se você estiver usando o Chrome ou o Internet Explorer, você encontrará o arquivo usando uma das seguintes estratégias:

   Para o Chrome, acesse **Gerenciador de Soluções > Documentos de Script > NomeDaPágina**.

    > [!NOTE]
    > Ao usar o Chrome, você poderá receber a mensagem **Nenhum código-fonte está disponível entre as marcas \<script>** . Não se preocupe. Basta continuar a depuração.

   Para o Internet Explorer, acesse **Gerenciador de Soluções > Documentos de Script > Windows Internet Explorer > NomeDaPágina**.

Para obter mais informações, confira [Depuração do lado do cliente de projetos ASP.NET no Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
