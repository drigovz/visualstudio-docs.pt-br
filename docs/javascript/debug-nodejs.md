---
title: Depurar um aplicativo JavaScript ou TypeScript
description: O Visual Studio fornece suporte para depuração de aplicativos JavaScript e TypeScript no Visual Studio
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: abfe762b354d11297aa4d0c574b8f0e0a081d349
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438002"
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

O Visual Studio fornece suporte de depuração somente para o Chrome e o Internet Explorer. Em alguns cenários, o depurador atinge automaticamente os pontos de interrupção no código JavaScript e TypeScript e em scripts inseridos em arquivos HTML.

Se a fonte for minificada ou criada por um transcompilador como o TypeScript ou o Babel, o uso de [mapas de origem](#generate_sourcemaps) será necessário para proporcionar a melhor experiência de depuração. Sem mapas de origem, você ainda poderá anexar o depurador a um script do lado do cliente em execução. No entanto, você só poderá definir e atingir pontos de interrupção no arquivo minificado ou transcompilado, não no arquivo de origem original. Por exemplo, em um aplicativo Vue.js, o script minificado é passado como uma cadeia de caracteres para uma instrução `eval`, e não há nenhuma maneira de executar esse código em etapas com eficiência usando o depurador do Visual Studio, a menos que você use mapas de origem. Em alguns cenários complexos de depuração, você também pode usar as Ferramentas para Desenvolvedores do Chrome ou as Ferramentas F12 do Microsoft Edge.

Para anexar o depurador por meio do Visual Studio e atingir pontos de interrupção no código do lado do cliente, o depurador normalmente precisa de ajuda para identificar o processo correto. Veja a seguir uma maneira de habilitar isso usando o Chrome.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Anexar o depurador ao script do lado do cliente usando o Chrome

1. Feche todas as janelas do Chrome.

    Essa ação é necessária antes de executar o Chrome no modo de depuração.

2. Abra o comando **Executar** do botão **Iniciar** do Windows (clique com o botão direito do mouse e escolha **Executar**) e digite o seguinte comando:

    `chrome.exe --remote-debugging-port=9222`

    Esse comando inicia o Chrome com a depuração habilitada.

    ::: moniker range=">=vs-2019"

    > [!NOTE]
    > Você também pode definir o sinalizador `--remote-debugging-port` na inicialização do navegador selecionando **Procurar Com...** > na barra de ferramentas **Depurar**, escolhendo **Adicionar** e, em seguida, definindo o sinalizador no campo **Argumentos**. Usar um nome amigável diferente para o navegador, como **Chrome com depuração**. Para obter detalhes, confira [Notas sobre a versão](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-preview#browser-cli-params-support).

    ::: moniker-end

3. Alterne para o Visual Studio e defina um ponto de interrupção no código-fonte. (Defina o ponto de interrupção em uma linha de código que permita pontos de interrupção, como uma instrução `return` ou uma declaração `var`).

    ![Definir um ponto de interrupção](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Caso precise localizar um código específico em um arquivo grande gerado, use **Ctrl**+**F** (**Editar** > **Localizar e Substituir** > **Localização Rápida**).

4. Com o Chrome selecionado como o destino de depuração no Visual Studio, pressione **Ctrl**+**F5** (**Depurar** > **Iniciar sem Depuração**) para executar o aplicativo no navegador.

    O aplicativo será aberto em uma nova guia do navegador.

    Se o Chrome estiver disponível em seu computador, mas não aparecer como uma opção, escolha **Procurar com** na lista suspensa de destinos de depuração e selecione Chrome como o destino padrão de navegador (escolha **Definir como padrão**).

5. Escolha **Depurar** > **Anexar ao Processo**.

6. Na caixa de diálogo **Anexar ao Processo**, escolha **Código do WebKit** no campo **Anexar a** e digite **Chrome** na caixa de filtro para filtrar o resultados da pesquisa.

    O **Código do WebKit** é o valor obrigatório para o Chrome, que é um navegador baseado em Webkit.

7. Selecione o processo do Chrome com a porta do host correta (1337, nesta ilustração) e selecione **Anexar**.

    ![Anexar ao processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Você sabe que o depurador foi anexado corretamente quando o Explorador do DOM e o Console do JavaScript são abertos no Visual Studio. Essas ferramentas de depuração são semelhantes às Ferramentas para Desenvolvedores do Chrome e às Ferramentas F12 do Microsoft Edge.

    > [!NOTE]
    > Se o depurador não for anexado e a mensagem "Não é possível anexar ao processo. Uma operação não é válida no estado atual", use o Gerenciador de Tarefas para fechar todas as instâncias do Chrome antes de iniciar o Chrome no modo de depuração. As extensões do Chrome podem estar em execução e impedindo o modo de depuração completa.

8. Se o código com o ponto de interrupção já tiver sido executado, atualize a página do navegador para atingir o ponto de interrupção.

    Enquanto estiver em pausa no depurador, você pode examinar o estado do aplicativo passando o mouse sobre as variáveis e usando as janelas do depurador. Você pode avançar o depurador percorrendo o código (**F5**, **F10** e **F11**).

    Para JavaScript minificado ou transcompilado, você pode atingir o ponto de interrupção no JavaScript transcompilado ou em sua localização mapeada no arquivo TypeScript (usando mapas de origem), dependendo do estado do navegador e do ambiente. De qualquer forma, você pode percorrer o código e examinar as variáveis.

    * Caso precise interromper o código em um arquivo TypeScript e não conseguir fazer isso, use a caixa de diálogo **Anexar ao Processo**, conforme descrito nas etapas anteriores para anexar o depurador. Em seguida, abra o arquivo TypeScript gerado dinamicamente no Gerenciador de Soluções abrindo **Documentos de Script** > **filename.tsx**, defina um ponto de interrupção e atualize a página no navegador (defina o ponto de interrupção em uma linha de código que permita pontos de interrupção, como a instrução `return` ou uma declaração `var`).

        Como alternativa, caso precise interromper o código em um arquivo TypeScript e não conseguir fazer isso, tente usar a instrução `debugger;` no arquivo TypeScript ou defina pontos de interrupção nas Ferramentas para Desenvolvedores do Chrome.

    * Caso precise interromper o código em um arquivo JavaScript transcompilado (por exemplo, *app-bundle.js*) e não conseguir fazer isso, remova o arquivo de mapa de origem, *filename.js.map*.

     > [!TIP]
     > Após anexar ao processo pela primeira vez seguindo estas etapas, você pode rapidamente anexar novamente ao mesmo processo escolhendo **Depurar** > **Reanexar ao Processo**.

## <a name="generate_sourcemaps"></a> Gerar mapas de origem para depuração

O Visual Studio tem a capacidade de usar e gerar mapas de origem em arquivos de origem JavaScript. Isso costuma ser necessário se a fonte é minificada ou criada por um transcompilador como o TypeScript ou o Babel. As opções disponíveis dependem do tipo de projeto.

* Por padrão, um projeto TypeScript no Visual Studio gera mapas de origem para você.

* Em um projeto JavaScript, é necessário gerar mapas de origem usando um empacotador como o webpack e um compilador como o compilador TypeScript (ou Babel), que pode ser adicionado ao projeto. Para o compilador TypeScript, também é necessário adicionar um arquivo *tsconfig.json*. Para obter um exemplo que mostra como fazer isso usando uma configuração básica de webpack, confira [Criar um aplicativo Node.js com o React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Caso não esteja familiarizado com mapas de origem, leia [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Introdução a mapas de origem JavaScript) antes de continuar.

Para definir configurações avançadas para mapas de origem, use um *tsconfig.json* ou as configurações do projeto em um projeto TypeScript, mas não ambos.

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

* **inlineSourceMap**: Emite um arquivo único com mapas de origem em vez de criar um mapa de origem separado para cada arquivo de origem.
* **inlineSources**: Emite o código-fonte juntamente com os mapas de origem em um arquivo único; exige a definição de *inlineSourceMap* ou *sourceMap*.
* **mapRoot**: Especifica a localização em que o depurador deve encontrar arquivos de mapa de origem (*.map*) em vez da localização padrão. Use esse sinalizador se os arquivos *.map* em tempo de execução precisarem estar em uma localização diferente dos arquivos *.js*. A localização especificada é inserida no mapa de origem para direcionar o depurador à localização dos arquivos *.map*.
* **sourceMap**: Gera um arquivo *.map* correspondente.
* **sourceRoot**: Especifica a localização em que o depurador deve encontrar arquivos TypeScript em vez das localizações de origem. Use esse sinalizador se as origens em tempo de execução precisarem estar em uma localização diferente da localização em tempo de design. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de origem.

Para obter mais detalhes sobre as opções do compilador, confira a página [Opções do compilador](https://www.typescriptlang.org/docs/handbook/compiler-options.html) no Manual do TypeScript.

### <a name="configure-source-maps-using-project-settings"></a>Configurar mapas de origem usando configurações do projeto

Defina também as configurações de mapa de origem usando as propriedades do projeto clicando com o botão direito do mouse no projeto e, em seguida, escolhendo **Projeto > Propriedades > Build TypeScript > Depuração**.

Estas configurações do projeto estão disponíveis.

* **Gerar mapas de origem** (equivalente a **sourceMap** em *tsconfig.json*): Gera o arquivo *.map* correspondente.
* **Especificar o diretório raiz de mapas de origem** (equivalente a **mapRoot** em *tsconfig.json*): Especifica a localização em que o depurador deve encontrar arquivos de mapa em vez das localizações geradas. Use esse sinalizador se os arquivos *.map* em tempo de execução precisarem estar em uma localização diferente dos arquivos .js. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de mapa.
* **Especificar o diretório raiz de arquivos TypeScript** (equivalente a **sourceRoot** em *tsconfig.json*): Especifica a localização em que o depurador deve encontrar arquivos TypeScript em vez das localizações de origem. Use esse sinalizador se os arquivos de origem em tempo de execução precisarem estar em uma localização diferente da localização em tempo de design. A localização especificada é inserida no mapa de origem para direcionar o depurador ao local em que se encontram os arquivos de origem.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Depurar JavaScript em arquivos dinâmicos usando o Razor (ASP.NET)

O Visual Studio fornece suporte de depuração somente para o Chrome e o Internet Explorer. Ele anexará automaticamente os pontos de interrupção ao JavaScript/TypeScript e aos scripts inseridos em arquivos HTML.

A depuração de arquivos gerados dinamicamente não é automática. Não é possível atingir automaticamente os pontos de interrupção em arquivos gerados com a sintaxe Razor (cshtml, vbhtml). Há duas abordagens que podem ser usadas para depurar esse tipo de arquivo:

* **Colocar a instrução `debugger;` no local em que você deseja interromper**: Isso interrompe a execução do script dinâmico e inicia sua depuração imediatamente, durante a criação.
* **Carregar a página e abrir o documento dinâmico no Visual Studio**: Você precisará abrir o arquivo dinâmico durante a depuração, definir o ponto de interrupção e atualizar a página para que esse método funcione. Dependendo se você estiver usando o Chrome ou o Internet Explorer, você encontrará o arquivo usando uma das seguintes estratégias:

   Para o Chrome, acesse **Gerenciador de Soluções > Documentos de Script > NomeDaPágina**.

    > [!NOTE]
    > Ao usar o Chrome, você poderá receber a mensagem **Nenhum código-fonte está disponível entre as marcas \<script>**. Não se preocupe. Basta continuar a depuração.

   Para o Internet Explorer, acesse **Gerenciador de Soluções > Documentos de Script > Windows Internet Explorer > NomeDaPágina**.

Para obter mais informações, confira [Depuração do lado do cliente de projetos ASP.NET no Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).