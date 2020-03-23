---
title: 'Tutorial: Código Debug C#'
description: Saiba como iniciar o depurador do Visual Studio, executar o código em etapas e inspecionar os dados.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 01/31/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ede47c9daf37011195d66c746498cdfc809d24b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77027248"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Tutorial: aprenda a depurar código C# usando o Visual Studio

Este artigo apresenta os recursos do depurador do Visual Studio passo a passo. Caso deseje obter uma exibição de nível superior das funcionalidades do depurador, confira [Introdução ao depurador](../../debugger/debugger-feature-tour.md). Quando você *depura seu aplicativo*, isso normalmente significa executar o aplicativo com o depurador anexado. Quando você faz isso, o depurador fornece várias maneiras de mostrar o que o código está fazendo enquanto é executado. Você pode percorrer o código e examinar os valores armazenados em variáveis, definir inspeções em variáveis para ver quando os valores mudam, examinar o caminho de execução do código, ver se um branch de código está em execução e assim por diante. Se esta for sua primeira tentativa de depurar um código, leia [Como depurar para iniciantes absolutos](../../debugger/debugging-absolute-beginners.md) antes continuar neste artigo.

Embora o aplicativo de demonstração esteja em C#, a maioria dos recursos são aplicáveis a C++, Visual Basic, F#, Python, JavaScript e outras linguagens compatíveis com o Visual Studio (o F# não é compatível com editar e continuar). F# e JavaScript não dão suporte à janela **Autos**). As capturas de tela estão em C#.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Iniciar o depurador e atingir os pontos de interrupção.
> * Aprender os comandos para percorrer o código no depurador
> * Inspecionar variáveis em dicas de dados e janelas do depurador
> * Examinar a pilha de chamadas

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=vs-2019"

Você deve ter o Visual Studio 2019 instalado e a carga de trabalho **de desenvolvimento multiplataforma .NET Core.**

::: moniker-end
::: moniker range="vs-2017"

Você deve ter o Visual Studio 2017 instalado e a carga de trabalho **de desenvolvimento multiplataforma .NET Core.**

::: moniker-end

::: moniker range="vs-2017"

Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do Visual Studio para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/downloads) do Visual Studio para instalá-lo gratuitamente.

::: moniker-end

Se você precisa instalar a carga de trabalho, mas já tem o Visual Studio, vá para **Ferramentas** > **Obter Ferramentas e Recursos...**, que abre o Visual Studio Installer. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **de desenvolvimento multiplataforma .NET Core** e escolha **Modificar**.

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto de aplicativo de console .NET Core. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada!

::: moniker range="vs-2017"

1. Abra o Visual Studio 2017.

2. Na barra de menu superior, escolha **Arquivo** > **Novo** > **Projeto**.

3. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda **C#** e escolha **.NET Core**. No painel central, escolha **Aplicativo de Console (.NET Core)**. Em seguida, nomeie o projeto *get-started-debugging*.

     Se você não vir o modelo de projeto do **Aplicativo de Console (.NET Core)**, escolha o link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

     O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.

::: moniker-end

::: moniker range="vs-2019"

1. Abra o Visual Studio 2019.

   Se a janela inicial não estiver aberta, escolha **Janela inicial de** **arquivo** > .

1. Na janela inicial, escolha **Criar um novo projeto**.

1. Na janela **Criar um novo projeto**, insira ou digite *console* na caixa de pesquisa. Em seguida, escolha **C#** na lista Linguagem de programação e, em seguida, escolha **Windows** na lista Plataforma. 

   Depois de aplicar os filtros de linguagem de programação e plataforma, escolha o modelo **Aplicativo de Console (.NET Core)** e, em seguida, escolha **Avançar**.

   ![Escolha o modelo C# para o aplicativo de console (.NET Core)](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Se não vir o modelo **Aplicativo de Console (.NET Core)**, você poderá instalá-lo da janela **Criar um novo projeto**. Na mensagem **Não encontrou o que precisa?**, escolha o link **Instalar mais ferramentas e recursos**. Em seguida, no Instalador do Visual Studio, escolha a carga de trabalho de **desenvolvimento multiplataforma do .NET Core**.

1. Na **Configure sua nova** janela de projeto, digite ou *digite GetStartedDebugging* na caixa **nome do Projeto.** Em seguida, escolha **Criar**.

   O Visual Studio abre seu novo projeto.
   
::: moniker-end

## <a name="create-the-application"></a>Criar o aplicativo

1. Em *Program.cs,* substitua todo o código padrão pelo seguinte código:

    ```csharp
    using System;
    class ArrayExample
    {
        static void Main()
        {
            char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h'};
            string name = "";
            int[] a = new int[10];
            for (int i = 0; i < letters.Length; i++)
            {
                name += letters[i];
                a[i] = i + 1;
                SendMessage(name, a[i]);
            }
            Console.ReadKey();
        }
        static void SendMessage(string name, int msg)
        {
            Console.WriteLine("Hello, " + name + "! Count to " + msg);
        }
    }
    ```

## <a name="start-the-debugger"></a>Inicie o depurador.

1. Pressione **F5** **(Debug > Iniciar Depuração)** ou o botão **Iniciar depuração** ![Iniciar depuração](../../debugger/media/dbg-tour-start-debugging.png "Iniciar Depuração") na barra de ferramentas Debug.

     **F5** inicia o aplicativo com o depurador anexado ao processo do aplicativo, mas nós ainda não fizemos nada de especial para examinar o código. Portanto, o aplicativo apenas é carregado e a saída do console é exibida.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     Neste tutorial, vamos analisar melhor esse aplicativo usando o depurador e analisar os recursos do depurador.

2. Pare o depurador pressionando o botão vermelho stop ![Stop Debugging](../../debugger/media/dbg-tour-stop-debugging.png "Parar Depuração") **(Shift** + **F5).**

3. Na janela do console, pressione uma tecla para fechar a janela do console.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

1. No loop `for` da função `Main`, defina um ponto de interrupção clicando na margem esquerda da seguinte linha de código:

    `name += letters[i];`

    Um ponto ![de ruptura](../../debugger/media/dbg-breakpoint.png "Ponto de interrupção") do círculo vermelho aparece onde você define o ponto de ruptura.

    Os breakpoints são um dos recursos mais básicos e essenciais da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não.

2. Pressione **F5** ou o botão **Iniciar depuração** ![Iniciar depuração](../../debugger/media/dbg-tour-start-debugging.png "Iniciar Depuração"), o aplicativo é iniciado e o depurador é executado até a linha de código onde você define o ponto de ruptura.

    ![Definir e atingir um ponto de interrupção](../csharp/media/get-started-set-breakpoint.png)

    A seta amarela representa a instrução na qual o depurador ficou em pausa, que também suspende a execução do aplicativo no mesmo ponto (essa instrução ainda não foi executada).

     Se o aplicativo ainda não estiver em execução, **F5** iniciará o depurador e o interromperá no primeiro ponto de interrupção. Caso contrário, **F5** continuará executando o aplicativo até o próximo ponto de interrupção.

    Os pontos de interrupção são um recurso útil quando você sabe qual linha ou seção de código deseja examinar em detalhes. Para obter informações sobre os diferentes tipos de breakpoints que você pode definir, como breakpoints condicional, consulte [Usando breakpoints](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar pelo código no depurador usando comandos de etapa

Geralmente, usamos atalhos de teclado aqui porque essa é uma boa maneira de executar o aplicativo rapidamente no depurador (os comandos equivalentes, como os comandos de menu, são mostrados entre parênteses).

1. Enquanto pausado `for` no `Main` loop no método, pressione **F11** (ou escolha **Debug > Step Into**) duas vezes para avançar para a chamada do `SendMessage` método.

     Depois de pressionar **f11** duas vezes, você deve estar nesta linha de código:

     `SendMessage(name, a[i]);`

1. Pressione **F11** mais uma `SendMessage` vez para entrar no método.

     O ponteiro amarelo `SendMessage` avança para o método.

     ![Use f11 para entrar no código](../csharp/media/get-started-f11.png "F10 Passo Em")

     F11 é o comando **Intervir**, que avança a execução do aplicativo uma instrução por vez. F11 é uma boa maneira de examinar o fluxo de execução com o máximo de detalhes. (Para mover mais rápido através do código, mostramos algumas outras opções também.) Por padrão, o depurador pula o código de não-usuário (se você quiser mais detalhes, consulte [Just My Code](../../debugger/just-my-code.md)).

     Vamos dizer que você está feito `SendMessage` examinando o método, e você quer sair do método, mas ficar no depurador. Você pode fazer isso usando o comando **Depuração Circular**.

1. Pressione **o Shift** + **F11** (ou **Debug > Step Out**).

     Este comando retoma a execução do aplicativo (e avança o depurador) até que o método ou função atual retorne.

     Você deve estar `for` de volta `Main` ao loop no `SendMessage` método, pausado na chamada do método.

1. Pressione **F11** várias vezes `SendMessage` até voltar ao método de chamada novamente.

1. Durante uma pausa na chamada do método, **pressione F10** (ou escolha **Depurar > Step Over**) uma vez.

     ![Use f10 para passar por cima do código](../csharp/media/get-started-step-over.png "F10 Step Over")

     Observe desta vez que o depurador `SendMessage` não entra no método. **F10** avança o depurador sem intervir em funções ou métodos no código do aplicativo (o código ainda é executado). Pressionando **F10** na chamada do método `SendMessage` (em vez de **F11**), ignoramos o código de implementação de `SendMessage` (que, no momento, talvez não seja de nosso interesse). Para obter mais informações sobre diferentes maneiras de mover-se através do seu código, consulte [Navegar código no depurador](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Navegar usando Executar até o Clique

1. Pressione **F5** para avançar para o ponto de ruptura novamente.

1. No editor de código, role para `Console.WriteLine` baixo `SendMessage` e passe o mouse sobre o método no método até que o botão **Executar para clicar** em Executar para ![clicar](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") apareça à esquerda. A dica de ferramenta para o botão mostra "Realizar a execução até aqui".

     ![Use o recurso Executar para clicar](../csharp/media/get-started-run-to-click.png "Executar com um Clique")

   > [!NOTE]
   > O botão **Executar até o Clique** é novo no [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. (Se você não ver o botão de seta verde, use **F11** neste exemplo para avançar o depurador para o lugar certo.)

2. Clique no botão **Executar para clicar** em Executar para ![clicar](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    O depurador avança `Console.WriteLine` para o método.

    O uso desse botão é semelhante à configuração de um ponto de interrupção temporário. **Executar até o Clique** é útil para abranger rapidamente uma região visível do código do aplicativo (você pode clicar em qualquer arquivo aberto).

## <a name="restart-your-app-quickly"></a>Reinicie o aplicativo rapidamente

Clique no botão **Restart** ![Restart App](../../debugger/media/dbg-tour-restart.png "RestartApp") na barra de ferramentas Debug **(Ctrl** + **Shift** + **F5**).

Ao pressionar **Reiniciar**, você economiza tempo em comparação com a opção de parar o aplicativo e reiniciar o depurador. O depurador é pausado no primeiro ponto de interrupção que é atingido pela execução do código.

O depurador pára novamente no ponto de `for` ruptura que você definiu anteriormente dentro do loop.

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

Os recursos que permitem que você inspecione variáveis são uns dos mais úteis do depurador e há diferentes maneiras de fazer isso. Muitas vezes, ao tentar depurar um problema, você tenta descobrir se as variáveis estão armazenando os valores que elas deveriam conter em um momento específico.

1. Enquanto pausado `name += letters[i]` na declaração, `letters` paire sobre a variável e você vê seu valor `char[10]`padrão, o valor do primeiro elemento na matriz, .

1. Expanda `letters` a variável para ver suas propriedades, que incluem todos os elementos que a variável contém.

1. Em seguida, paire sobre a `name` variável, e você vê seu valor atual, uma seqüência vazia.

1. Pressione **F5** (ou **Debug** > **Continue)** algumas vezes para `for` iterar várias vezes através do `name` loop, parando novamente no ponto de quebra e pairando sobre a variável cada vez para verificar seu valor.

     ![Ver uma dica de dados](../csharp/media/get-started-data-tip.gif "Exibir uma dica de dados")

     O valor da variável muda a cada `for` iteração `f`do `fr`loop, `fre`mostrando valores de , então , então , e assim por diante.

     Muitas vezes, durante a depuração, você deseja uma maneira rápida de verificar valores de propriedade em variáveis, para ver se eles estão armazenando os valores que você espera que armazenem. As dicas de dados são uma boa maneira de fazer isso.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com as janelas Autos e Locais

1. Examine a janela **Autos** na parte inferior do editor de códigos.

    Se estiver fechado, abra-o enquanto estiver pausado no depurador, escolhendo **Debug** > **Windows** > **Autos**.

    Na janela **Autos**, veja as variáveis e seus valores atuais. A janela **Autos** mostra todas as variáveis usadas na linha atual ou a linha anterior (verifique a documentação para saber o comportamento específico a uma linguagem).

1. Em seguida, examine a janela **Locais**, em uma guia ao lado da janela **Autos**.

1. Expanda `letters` a variável para mostrar os elementos que ela contém.

     ![Inspecione variáveis na janela Locais](../csharp/media/get-started-locals-window.png "Janela Locais")

    A janela **Locais** mostra as variáveis que estão no [escopo](https://www.wikipedia.org/wiki/Scope_(computer_science)) atual, ou seja, o contexto de execução atual.

## <a name="set-a-watch"></a>Definir uma inspeção

1. Na janela principal do editor de `name` código, clique com o botão direito do mouse na variável e escolha **Adicionar relógio**.

    A janela **Inspeção** é aberta na parte inferior do editor de códigos. Você pode usar uma janela **Inspeção** para especificar uma variável (ou uma expressão) que deseja acompanhar.

    Agora, você tem um `name` relógio definido na variável, e você pode ver sua mudança de valor à medida que você se move através do depurador. Ao contrário das outras janelas de variáveis, a janela **Inspeção** sempre mostra as variáveis que você está inspecionando (eles ficam esmaecidas quando estão fora do escopo).

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

1. Durante a pausa no loop `for`, clique na janela **Pilha de Chamadas** que fica aberta por padrão no painel inferior direito.

    Se estiver fechado, abra-o durante a pausa no depurador, escolhendo **Debug** > **Windows** > **Call Stack**.

2. Clique em **F11** algumas vezes até ver a `SendMessage` pausa do depurador no método. Examine a janela **Pilha de Chamadas**.

    ![Examinar a pilha de chamadas](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    A janela **Pilha de Chamadas** mostra a ordem em que os métodos e as funções são chamados. A linha superior mostra a função atual (o método `SendMessage` neste aplicativo). A segunda linha mostra que `SendMessage` foi chamado por meio do método `Main` e assim por diante.

   > [!NOTE]
   > A janela **Pilha de Chamadas** é semelhante à perspectiva de Depuração em alguns IDEs, como o Eclipse.

    A pilha de chamadas é uma boa maneira de examinar e entender o fluxo de execução de um aplicativo.

    Você pode clicar duas vezes em uma linha de código para examinar esse código-fonte. Isso também altera o escopo atual que está sendo inspecionado pelo depurador. Essa ação não avança o depurador.

    Você também pode usar os menus acessados ao clicar com o botão direito do mouse na janela **Pilha de Chamadas** para fazer outras coisas. Por exemplo, você pode inserir pontos de interrupção em funções especificadas, avançar o depurador usando **Executar até o Cursor** e examinar o código-fonte. Para obter mais informações, confira [Como examinar a pilha de chamadas](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Alterar o fluxo de execução

1. Pressione **F11** duas `Console.WriteLine` vezes para executar o método.

1. Com o depurador pausado na chamada do `SendMessage` método, use o mouse para pegar a seta amarela (o `Console.WriteLine`ponteiro de execução) à esquerda e mover a seta amarela para cima de uma linha, de volta para .

1. Pressione **F11**.

    O depurador executa novamente o método `Console.WriteLine` (você vê isso na saída da janela do console).

    Alterando o fluxo de execução, você pode fazer coisas como testar caminhos de execução de código diferentes ou executar novamente o código sem reiniciar o depurador.

    > [!WARNING]
    > Geralmente, você precisa ter cuidado com esse recurso. Um aviso é exibido na dica de ferramenta. Outros avisos também podem ser exibidos. Ao mover o ponteiro não é possível reverter o aplicativo para um estado anterior.

1. Pressione **F5** para continuar a execução do aplicativo.

    Parabéns por concluir este tutorial.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Talvez você queira obter uma visão geral dos recursos do depurador, com links para mais informações.

> [!div class="nextstepaction"]
> [Primeiro olhe para o depurador](../../debugger/debugger-feature-tour.md)
