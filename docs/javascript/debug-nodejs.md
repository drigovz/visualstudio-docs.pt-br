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
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678968"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Depurar um aplicativo JavaScript ou TypeScript no Visual Studio

Depure o código JavaScript e TypeScript usando o Visual Studio. Defina e atinja pontos de interrupção, anexe o depurador, inspecione variáveis, exiba a pilha de chamadas e use outras funcionalidades de depuração.

> [!TIP]
> Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/downloads/) do Visual Studio para instalá-lo gratuitamente. Dependendo do tipo de desenvolvimento de aplicativo que você estiver fazendo, talvez você precise instalar a **carga de trabalho de desenvolvimento em Node.js** com o Visual Studio.

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
O Visual Studio oferece suporte de depuração do lado do cliente apenas para Chrome e Microsoft Edge (Chromium). Em alguns cenários, o depurador atinge automaticamente os pontos de interrupção no código JavaScript e TypeScript e em scripts inseridos em arquivos HTML. Para depurar o script do lado do cliente em ASP.NET aplicativos, consulte o post do blog [Debug JavaScript no Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) e este [post para o Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome). Para depurar TypeScript no ASP.NET Core, consulte [Criar um aplicativo ASP.NET Core com TypeScript](tutorial-aspnet-with-typescript.md).
::: moniker-end
::: moniker range="vs-2017"
O Visual Studio oferece suporte de depuração do lado do cliente apenas para chrome e Internet Explorer. Em alguns cenários, o depurador atinge automaticamente os pontos de interrupção no código JavaScript e TypeScript e em scripts inseridos em arquivos HTML. Para depurar o script do lado do cliente em ASP.NET aplicativos, consulte o blog post [Depuração do lado do cliente de projetos de ASP.NET no Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Para aplicações que não sejam ASP.NET, siga as etapas descritas aqui.

### <a name="prepare-your-app-for-debugging"></a>Prepare seu aplicativo para depuração

Se a fonte for minificada ou criada por um transcompilador como o TypeScript ou o Babel, o uso de [mapas de origem](#generate_source_maps) será necessário para proporcionar a melhor experiência de depuração. Sem mapas de origem, você ainda poderá anexar o depurador a um script do lado do cliente em execução. No entanto, você só poderá definir e atingir pontos de interrupção no arquivo minificado ou transcompilado, não no arquivo de origem original. Por exemplo, em um aplicativo Vue.js, o script minificado é passado como uma cadeia de caracteres para uma instrução `eval`, e não há nenhuma maneira de executar esse código em etapas com eficiência usando o depurador do Visual Studio, a menos que você use mapas de origem. Em cenários complexos de depuração, você também pode usar o Chrome Developer Tools ou o F12 Tools para o Microsoft Edge.

Para obter ajuda para gerar mapas de origem, consulte [Gerar mapas de origem para depuração](#generate_source_maps).

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a>Prepare o navegador para depuração

::: moniker range=">=vs-2019"
Para este cenário, use o Microsoft Edge (Chromium), atualmente chamado **Microsoft Edge Beta** no IDE, ou Chrome.
::: moniker-end
::: moniker range="vs-2017"
Para este cenário, use o Chrome.
::: moniker-end

1. Feche todas as janelas para o navegador alvo.

   Outras instâncias do navegador podem impedir que o navegador seja aberto com a depuração ativada. (As extensões do navegador podem estar executando e impedindo o modo de depuração total, então você pode precisar abrir o Gerenciador de tarefas para encontrar instâncias inesperadas do Chrome.)

   ::: moniker range=">=vs-2019"
   Para o Microsoft Edge (Chromium), também desligue todas as instâncias do Chrome. Como ambos os navegadores usam a base de código de cromo, isso dá os melhores resultados.
   ::: moniker-end

2. Inicie seu navegador com a depuração ativada.

    ::: moniker range=">=vs-2019"
    A partir do Visual Studio 2019, você pode definir `--remote-debugging-port=9222` o sinalizador no lançamento do navegador selecionando Procurar **com...** > na barra de ferramentas **Debug,** depois escolhendo **Adicionar**, e, em seguida, definir o sinalizador no campo **Argumentos.** Use um nome amigável diferente para o navegador, como **Edge com Depuração** ou **Chrome com Depuração**. Para obter detalhes, confira [Notas sobre a versão](/visualstudio/releases/2019/release-notes-v16.2).

    ![Defina seu navegador para abrir com a depuração ativada](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternativamente, abra o comando **Executar** a partir do **botão** Iniciar do Windows (clique com o botão direito do mouse e escolha **Executar),** e digite o seguinte comando:

    `msedge --remote-debugging-port=9222`

    ou

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Abra o comando **Executar** do botão **Iniciar** do Windows (clique com o botão direito do mouse e escolha **Executar**) e digite o seguinte comando:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Isso inicia o seu navegador com a depuração ativada.

    O aplicativo ainda não está sendo executado, então você recebe uma página de navegador vazia.

### <a name="attach-the-debugger-to-client-side-script"></a>Anexar o depurador ao script do lado do cliente

Para anexar o depurador do Visual Studio e atingir pontos de interrupção no código do lado do cliente, o depurador precisa de ajuda para identificar o processo correto. Esta é uma maneira de permitir isso.

1. Mude para o Visual Studio e, em seguida, defina um ponto de ruptura em seu código-fonte, que pode ser um arquivo JavaScript, arquivo TypeScript ou um arquivo JSX. (Defina o ponto de interrupção em uma linha de código que permita pontos de interrupção, como uma declaração de retorno ou uma declaração de VAR.)

    ![Definir um ponto de interrupção](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Para encontrar o código específico em um arquivo transcompilado, use **Ctrl**+**F** **(Editar** > **encontrar e substituir o** > **quick find**).

    Para o código do lado do cliente, para atingir um ponto de ruptura em um arquivo TypeScript, o arquivo *.vue*ou JSX normalmente requer o uso de mapas de [origem](#generate_source_maps). Um mapa de origem deve ser configurado corretamente para suportar a depuração no Visual Studio.

2. Selecione seu navegador de destino como alvo de depuração no Visual Studio e pressione **Ctrl**+**F5** **(Debug** > **Start Without Debugging)** para executar o aplicativo no navegador.

    ::: moniker range=">=vs-2019"
    Se você criou uma configuração de navegador com um nome amigável, escolha-o como seu destino de depuração.
    ::: moniker-end

    O aplicativo será aberto em uma nova guia do navegador.

3. Escolha **Depurar** > **anexar ao processo**.

    > [!TIP]
    > A partir do Visual Studio 2017, uma vez anexado ao processo pela primeira vez seguindo essas etapas, você pode rapidamente reconectar ao mesmo processo, escolhendo **Debug** > **Reattach to Process**.

4. Na caixa de diálogo **Anexar ao processo,** obtenha uma lista filtrada de instâncias do navegador às as que você pode anexar.
    ::: moniker range=">=vs-2019"
    No Visual Studio 2019, escolha o depurador correto para o seu navegador de destino, **JavaScript (Chrome)** ou **JavaScript (Microsoft Edge - Chromium)** no **Attach to** field, **digite cromo** ou **borda** na caixa de filtro para filtrar os resultados da pesquisa.
    ::: moniker-end
    ::: moniker range="vs-2017"
    No Visual Studio 2017, escolha o **código Webkit** no campo **Anexar ao** campo, digite **cromo** na caixa de filtro para filtrar os resultados da pesquisa.
    ::: moniker-end

5. Selecione o processo do navegador com a porta host correta (host local neste exemplo) e selecione **'Anexar '''''''''''''**

    A porta (por exemplo, 1337) também pode aparecer no campo **Título** para ajudá-lo a selecionar a instância correta do navegador.

    ::: moniker range=">=vs-2019"
    O exemplo a seguir mostra como isso parece para o navegador Microsoft Edge (Chromium).

    ![Anexar ao processo](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Anexar ao processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Você sabe que o depurador foi anexado corretamente quando o Explorador do DOM e o Console do JavaScript são abertos no Visual Studio. Essas ferramentas de depuração são semelhantes às Ferramentas para Desenvolvedores do Chrome e às Ferramentas F12 do Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Se o depurador não for anexado e você ver a mensagem "Falha ao iniciar adaptador de depuração" ou "Não é possível anexar ao processo. Uma operação não é legal no estado atual.", use o Gerenciador de Tarefas do Windows para fechar todas as instâncias do navegador de destino antes de iniciar o navegador no modo de depuração. As extensões do navegador podem estar sendo executados e impedindo o modo de depuração total.

6. Como o código com o ponto de partida pode já ter sido executado, atualize a página do seu navegador. Se necessário, tome medidas para fazer com que o código com o ponto de ruptura seja executado.

    Enquanto estiver em pausa no depurador, você pode examinar o estado do aplicativo passando o mouse sobre as variáveis e usando as janelas do depurador. Você pode avançar o depurador percorrendo o código (**F5**, **F10** e **F11**). Para obter mais informações sobre recursos básicos de depuração, consulte [Primeiro, veja o depurador](../debugger/debugger-feature-tour.md).

    Você pode atingir o ponto de ruptura em um arquivo *.js* transcompilado ou no arquivo de origem, dependendo do tipo de aplicativo, quais passos você seguiu anteriormente e outros fatores, como o estado do seu navegador. De qualquer forma, você pode percorrer o código e examinar as variáveis.

   * Se você precisar invadir o código em um arquivo de código, JSX ou *.vue* e não conseguir fazê-lo, certifique-se de que seu ambiente esteja configurado corretamente, conforme descrito na seção [Solução de problemas.](#troubleshooting_source_maps)

   * Se você precisar invadir o código em um arquivo JavaScript transcompilado (por exemplo, *app-bundle.js*) e não conseguir fazê-lo, remova o arquivo do mapa de origem, *filename.js.map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a>Pontos de interrupção de solução de problemas e mapas de origem

Se você precisar invadir o código em um arquivo fonte TypeScript ou JSX e não puder fazê-lo, use **'Anexar ao processo'** conforme descrito nas etapas anteriores para anexar o depurador. Certifique-se de que seu ambiente está configurado corretamente:

* Você fechou todas as instâncias do navegador, incluindo extensões do Chrome (usando o Gerenciador de tarefas), para que você possa executar o navegador no modo de depuração.
      
* Certifique-se [de iniciar o navegador no modo de depuração](#prepare_the_browser_for_debugging).

* Certifique-se de que o arquivo do mapa de origem inclua o caminho relativo correto ao seu arquivo de origem e que ele não inclua prefixos não suportados, como *webpack:///,* o que impede que o depurador do Visual Studio localize um arquivo de origem. Por exemplo, uma referência como *webpack:///.app.tsx* pode ser corrigida para *./app.tsx*. Você pode fazer isso manualmente no arquivo do mapa de origem (o que é útil para testes) ou através de uma configuração de compilação personalizada. Para obter mais informações, consulte [Gerar mapas de origem para depuração](#generate_source_maps).

Alternativamente, se você precisar invadir o código em um arquivo de origem (por exemplo, *app.tsx*) e não conseguir fazê-lo, tente usar a `debugger;` declaração no arquivo de origem ou defina pontos de interrupção nas Ferramentas do Desenvolvedor Do Chrome (ou Ferramentas F12 para o Microsoft Edge) em vez disso.

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> Gerar mapas de origem para depuração

O Visual Studio tem a capacidade de usar e gerar mapas de origem em arquivos de origem JavaScript. Isso costuma ser necessário se a fonte é minificada ou criada por um transcompilador como o TypeScript ou o Babel. As opções disponíveis dependem do tipo de projeto.

* Por padrão, um projeto TypeScript no Visual Studio gera mapas de origem para você. Para obter mais informações, consulte [Configure mapas de origem usando um arquivo tsconfig.json](#configure_source_maps).

* Em um projeto JavaScript, você pode gerar mapas de origem usando um bundler como webpack e um compilador como o compilador TypeScript (ou Babel), que você pode adicionar ao seu projeto. Para o compilador TypeScript, você também deve adicionar um arquivo *tsconfig.json* e definir a `sourceMap` opção compilador. Para obter um exemplo que mostra como fazer isso usando uma configuração básica de webpack, confira [Criar um aplicativo Node.js com o React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Caso não esteja familiarizado com mapas de origem, leia [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Introdução a mapas de origem JavaScript) antes de continuar. 

Para definir configurações avançadas para mapas de origem, use um *tsconfig.json* ou as configurações do projeto em um projeto TypeScript, mas não ambos.

Para habilitar a depuração usando o Visual Studio, você precisa ter certeza de que as referências ao seu arquivo de origem no mapa de origem estão corretas (isso pode exigir testes). Por exemplo, se você estiver usando webpack, as referências no arquivo do mapa de origem incluem o prefixo *webpack:///,* que impede o Visual Studio de encontrar um arquivo de origem TypeScript ou JSX. Especificamente, quando você corrige isso para fins de depuração, a referência ao arquivo de origem (como *app.tsx),* deve ser alterada de algo como *webpack:///./app.tsx* para algo como *./app.tsx*, que permite a depuração (o caminho é relativo ao seu arquivo de origem). O exemplo a seguir mostra como você pode configurar mapas de origem no webpack, que é um dos empacotadores mais comuns, para que eles trabalhem com o Visual Studio.

(Somente webpack) Se você estiver configurando o ponto de ruptura em um TypeScript de arquivo JSX (em vez de um arquivo JavaScript transcompilado), você precisa atualizar a configuração do webpack. Por exemplo, em *webpack-config.js,* talvez seja necessário substituir o seguinte código:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

por este código:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Esta é uma configuração somente de desenvolvimento para permitir a depuração do código do lado do cliente no Visual Studio.

Para cenários complicados, as ferramentas do navegador **(F12)** às vezes funcionam melhor para depuração, porque não exigem alterações em prefixos personalizados.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a>Configure mapas de origem usando um arquivo tsconfig.json

Se você adicionar um arquivo *tsconfig.json* ao projeto, o Visual Studio tratará a raiz do diretório como um projeto TypeScript. Para adicionar o arquivo, clique com o botão direito do mouse no projeto no Solution Explorer e, em seguida, escolha **Adicionar > Novo Item > TypeScript Arquivo de configuração JSON**. Um arquivo *tsconfig.json* como o mostrado a seguir é adicionado ao projeto.

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

* **inlineSourceMap**: Emita um único arquivo com mapas de origem em vez de criar um mapa de origem separado para cada arquivo de origem.
* **inlineSources**: Emita a fonte ao lado dos mapas de origem dentro de um único arquivo; requer *inlineSourceMap* ou *sourceMap* a serem definidos.
* **mapRoot**: Especifica o local onde o depurador deve encontrar arquivos de mapa de origem *(.map)* em vez do local padrão. Use esse sinalizador se os arquivos *.map* em tempo de execução precisarem estar em uma localização diferente dos arquivos *.js*. A localização especificada é inserida no mapa de origem para direcionar o depurador à localização dos arquivos *.map*.
* **sourceMap**: Gera um arquivo *.map* correspondente.
* **sourceRoot**: Especifica o local onde o depurador deve encontrar arquivos TypeScript em vez dos locais de origem. Use esse sinalizador se as origens em tempo de execução precisarem estar em uma localização diferente da localização em tempo de design. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de origem.

Para obter mais detalhes sobre as opções do compilador, confira a página [Opções do compilador](https://www.typescriptlang.org/docs/handbook/compiler-options.html) no Manual do TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configure mapas de origem usando configurações de projeto (projeto TypeScript)

Defina também as configurações de mapa de origem usando as propriedades do projeto clicando com o botão direito do mouse no projeto e, em seguida, escolhendo **Projeto > Propriedades > Build TypeScript > Depuração**.

Estas configurações do projeto estão disponíveis.

* **Gerar mapas de origem** (equivalente ao **sourceMap** em *tsconfig.json*): Gera arquivo *.map* correspondente.
* **Especificar diretório raiz de mapas de origem** (equivalente a **mapRoot** em *tsconfig.json*): Especifica o local onde o depurador deve encontrar arquivos de mapa em vez dos locais gerados. Use esse sinalizador se os arquivos *.map* em tempo de execução precisarem estar em uma localização diferente dos arquivos .js. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de mapa.
* **Especificar diretório raiz de arquivos TypeScript** (equivalente a **sourceRoot** em *tsconfig.json*): Especifica o local onde o depurador deve encontrar arquivos TypeScript em vez de locais de origem. Use esse sinalizador se os arquivos de origem em tempo de execução precisarem estar em uma localização diferente da localização em tempo de design. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de origem.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Depurar JavaScript em arquivos dinâmicos usando o Razor (ASP.NET)

::: moniker range=">=vs-2019"
A partir do Visual Studio 2019, o Visual Studio oferece suporte de depuração apenas para Chrome e Microsoft Edge (Chromium).
::: moniker-end
::: moniker range="vs-2017"
O Visual Studio fornece suporte de depuração somente para o Chrome e o Internet Explorer.
::: moniker-end

No entanto, você não pode atingir automaticamente pontos de interrupção em arquivos gerados com sintaxe de Navalha (cshtml, vbhtml). Há duas abordagens que podem ser usadas para depurar esse tipo de arquivo:

* **Coloque `debugger;` a declaração onde deseja quebrar**: Isso faz com que o script dinâmico interrompa a execução e comece a depurar imediatamente enquanto ele está sendo criado.
* **Carregue a página e abra o documento dinâmico no Visual Studio**: Você precisará abrir o arquivo dinâmico durante a depuração, definir seu ponto de ruptura e atualizar a página para que este método funcione. Dependendo se você estiver usando o Chrome ou o Internet Explorer, você encontrará o arquivo usando uma das seguintes estratégias:

   Para o Chrome, acesse **Gerenciador de Soluções > Documentos de Script > NomeDaPágina**.

    > [!NOTE]
    > Ao usar o Chrome, você poderá receber a mensagem **Nenhum código-fonte está disponível entre as marcas \<script>**. Não se preocupe. Basta continuar a depuração.

   ::: moniker range=">=vs-2019"
   Para o Microsoft Edge (Chromium), use o mesmo procedimento que o Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   Para o Internet Explorer, acesse **Gerenciador de Soluções > Documentos de Script > Windows Internet Explorer > NomeDaPágina**.
   ::: moniker-end

Para obter mais informações, confira [Depuração do lado do cliente de projetos ASP.NET no Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
