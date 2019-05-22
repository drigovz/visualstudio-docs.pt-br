---
title: 'Tutorial: Depurar o código do Visual Basic'
description: Saiba como iniciar o depurador do Visual Studio, executar o código em etapas e inspecionar os dados.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
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
ms.openlocfilehash: 070de03f56f6d9d10a9e6a41516ffcb67837e90e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680304"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Tutorial: Aprenda a depurar o código do Visual Basic usando o Visual Studio

Este artigo apresenta os recursos do depurador do Visual Studio passo a passo. Caso deseje obter uma exibição de nível superior das funcionalidades do depurador, confira [Introdução ao depurador](../../debugger/debugger-feature-tour.md). Quando você *depura seu aplicativo*, isso normalmente significa executar o aplicativo com o depurador anexado. Quando você faz isso, o depurador fornece várias maneiras de mostrar o que o código está fazendo enquanto é executado. Você pode percorrer o código e examinar os valores armazenados em variáveis, definir inspeções em variáveis para ver quando os valores mudam, examinar o caminho de execução do código, ver se um branch de código está em execução e assim por diante. Se esta for sua primeira tentativa de depurar um código, leia [Como depurar para iniciantes absolutos](../../debugger/debugging-absolute-beginners.md) antes continuar neste artigo.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Iniciar o depurador e atingir os pontos de interrupção.
> * Aprender os comandos para percorrer o código no depurador
> * Inspecionar variáveis em dicas de dados e janelas do depurador
> * Examinar a pilha de chamadas

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=vs-2019"

Você precisa ter o Visual Studio 2019 instalado e a carga de trabalho de **desenvolvimento para desktop com .NET**.

::: moniker-end
::: moniker range="vs-2017"

Você precisa ter o Visual Studio 2017 instalado e a carga de trabalho de **desenvolvimento para desktop com .NET**.

::: moniker-end

::: moniker range="vs-2017"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para instalá-lo gratuitamente.

::: moniker-end

Caso precise instalar a carga de trabalho, mas já tiver o Visual Studio, acesse **Ferramentas** > **Obter Ferramentas e Funcionalidades...**, que abre o Instalador do Visual Studio. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de área de trabalho do .NET** e, em seguida, selecione **Modificar**.

## <a name="create-a-project"></a>Criar um projeto

1. Abra o Visual Studio.

    ::: moniker range=">=vs-2019"
    Pressione **Esc** para fechar a janela de início. Digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **visual basic**, escolha **Modelos** e, em seguida, escolha **Criar novo projeto de Aplicativo de Console (.NET Framework)**. Na caixa de diálogo que aparece, digite um nome como **iniciar-depuração** e, em seguida, escolha **Criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**. No painel esquerdo da caixa de diálogo **Novo projeto**, em **Visual Basic**, escolha **Área de Trabalho do Windows** e, em seguida, no painel central, escolha **Aplicativo de Console (.NET Framework)**. Em seguida, digite um nome como **get-started-debugging** e clique em **OK**.
    ::: moniker-end

    Caso não veja o modelo de projeto **Aplicativo de Console (.NET Framework)**, acesse **Ferramentas** > **Obter Ferramentas e Recursos...**, que abre o Instalador do Visual Studio. Escolha a carga de trabalho **Desenvolvimento de área de trabalho do .NET** e, em seguida, selecione **Modificar**.

    O Visual Studio cria o projeto.

1. Em *Module1.vb*, substitua o código a seguir

    ```vb
    Module Module1

        Sub Main()
        End Sub

    End Module
    ```

    com este código:

    ```vb
    Imports System
    Imports System.Collections.Generic

    Public Class Shape

      ' A few example members
        Public Property X As Integer
            Get
                Return X
            End Get
            Set
            End Set
        End Property

        Public Property Y As Integer
            Get
                Return Y
            End Get
            Set
            End Set
        End Property

        Public Property Height As Integer
            Get
                Return Height
            End Get
            Set
            End Set
        End Property

        Public Property Width As Integer
            Get
                Return Width
            End Get
            Set
            End Set
        End Property

        ' Virtual method
        Public Overridable Sub Draw()
            Console.WriteLine("Performing base class drawing tasks")
        End Sub
    End Class

    Public Class Circle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a circle...
            Console.WriteLine("Drawing a circle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Rectangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Triangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a triangle...
            Console.WriteLine("Drawing a trangle")
            MyBase.Draw()
        End Sub
    End Class

    Module Module1

        Sub Main(ByVal args() As String)

            Dim shapes = New List(Of Shape) From
            {
                New Rectangle,
                New Triangle,
                New Circle
            }

            For Each shape In shapes
                shape.Draw()
            Next
            ' Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.")
            Console.ReadKey()

        End Sub

    End Module

    ' Output:
    '    Drawing a rectangle
    '    Performing base class drawing tasks
    '    Drawing a triangle
    '    Performing base class drawing tasks
    '    Drawing a circle
    '    Performing base class drawing tasks
    ```

## <a name="start-the-debugger"></a>Inicie o depurador.

1. Pressione **F5** (**Depurar > Iniciar Depuração**) ou o botão **Iniciar Depuração** ![Iniciar Depuração](../../debugger/media/dbg-tour-start-debugging.png "Iniciar Depuração") na barra de ferramentas Depurar.

     **F5** inicia o aplicativo com o depurador anexado ao processo do aplicativo, mas nós ainda não fizemos nada de especial para examinar o código. Portanto, o aplicativo apenas é carregado e a saída do console é exibida.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     Neste tutorial, vamos analisar melhor esse aplicativo usando o depurador e analisar os recursos do depurador.

2. Pare o depurador pressionando o botão de parada vermelho ![Parar Depuração](../../debugger/media/dbg-tour-stop-debugging.png "Parar Depuração").

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

1. No loop `For Each` da função `Main`, defina um ponto de interrupção clicando na margem esquerda da seguinte linha de código:

    `shape.Draw()`

    Aparece um círculo vermelho no qual você definiu o ponto de interrupção.

    ![Definir um ponto de interrupção](../visual-basic/media/get-started-set-breakpoint-vb.png)

    Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não.

2. Pressione **F5** ou o botão **Iniciar Depuração** ![Iniciar Depuração](../../debugger/media/dbg-tour-start-debugging.png "Iniciar Depuração"). O aplicativo será iniciado e o depurador executará a linha de código em que você definiu o ponto de interrupção.

    ![Atingir um ponto de interrupção](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    A seta amarela representa a instrução na qual o depurador ficou em pausa, que também suspende a execução do aplicativo no mesmo ponto (essa instrução ainda não foi executada).

     Se o aplicativo ainda não estiver em execução, **F5** iniciará o depurador e o interromperá no primeiro ponto de interrupção. Caso contrário, **F5** continuará executando o aplicativo até o próximo ponto de interrupção.

    Os pontos de interrupção são um recurso útil quando você sabe qual linha ou seção de código deseja examinar em detalhes.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar pelo código no depurador usando comandos de etapa

Geralmente, usamos atalhos de teclado aqui porque essa é uma boa maneira de executar o aplicativo rapidamente no depurador (os comandos equivalentes, como os comandos de menu, são mostrados entre parênteses).

1. Enquanto estiver em pausa na chamada de método `shape.Draw` na função `Main`, pressione **F11** (ou escolha **Depurar > Intervir**) para avançar no código até a classe `Rectangle`.

     ![Usar F11 para intervir no código](../visual-basic/media/get-started-f11-vb.png "F11 Intervir")

     F11 é o comando **Intervir**, que avança a execução do aplicativo uma instrução por vez. F11 é uma boa maneira de examinar o fluxo de execução com o máximo de detalhes. (Também vamos mostrar algumas outras opções para percorrer o código com mais rapidez.) Por padrão, o depurador ignora as partes do código que não são do usuário (se quiser saber mais detalhes, confira [Apenas Meu Código](../../debugger/just-my-code.md)).

2. Pressione **F10** (ou escolha **Depurar > Depuração Parcial**) algumas vezes até que o depurador pare na chamada de método `MyBase.Draw`. Em seguida, pressione **F10** mais uma vez.

     ![Usar F10 para Depuração Parcial do código](../visual-basic/media/get-started-step-over-vb.png "F10 Depuração Parcial")

     Observe neste momento que o depurador não intervém no método `Draw` da classe base (`Shape`). **F10** avança o depurador sem intervir em funções ou métodos no código do aplicativo (o código ainda é executado). Pressionando **F10** na chamada do método `MyBase.Draw` (em vez de **F11**), ignoramos o código de implementação de `MyBase.Draw` (que, no momento, talvez não seja de nosso interesse).

## <a name="navigate-code-using-run-to-click"></a>Navegar usando Executar até o Clique

1. No editor de códigos, role para baixo e passe o mouse sobre o método `Console.WriteLine` na classe `Triangle` até que o botão verde **Executar até o Clique** ![Executar até o Clique](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") apareça à esquerda. A dica de ferramenta para o botão mostra "Realizar a execução até aqui".

     ![Usar o recurso Executar até o Clique](../visual-basic/media/get-started-run-to-click-vb.png "Executar até o Clique")

   > [!NOTE]
   > O botão **Executar até o Clique** é novo no [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Se o botão de seta verde não for exibido, use **F11**, neste exemplo, para avançar o depurador até o lugar certo.

2. Clique no botão **Executar até o Clique** ![Executar até o Clique](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    O uso desse botão é semelhante à configuração de um ponto de interrupção temporário. **Executar até o Clique** é útil para abranger rapidamente uma região visível do código do aplicativo (você pode clicar em qualquer arquivo aberto).

    O depurador avança para a implementação do método `Console.WriteLine` da classe `Triangle`.

    Durante a pausa, você poderá observar um erro de digitação! A saída "Drawing a trangle" contém um erro de digitação. Podemos corrigir isso aqui mesmo enquanto o aplicativo é executado no depurador.

## <a name="edit-code-and-continue-debugging"></a>Editar o código e continuar a depuração

1. Clique em "Drawing a trangle" e digite uma correção, alterando "trangle" para "triangle".

1. Pressione **F11** uma vez e veja que o depurador avançará novamente.

    > [!NOTE]
    > Dependendo de qual tipo de código você editar no depurador, será exibida uma mensagem de aviso. Em alguns cenários, o código precisará ser recompilado para que você possa continuar.

## <a name="step-out"></a>Depuração circular

Digamos que você termine de examinar o método `Draw` na classe `Triangle` e queira sair da função, mas continuar no depurador. Você pode fazer isso usando o comando **Depuração Circular**.

1. Pressione **Shift** + **F11** (ou **Depurar > Depuração Circular**).

     Este comando retoma a execução do aplicativo (e avança o depurador) até que a função atual retorne.

     Você deve ter voltado ao loop `For Each` no método `Main`.

## <a name="restart-your-app-quickly"></a>Reinicie o aplicativo rapidamente

Clique no botão **Reiniciar** ![Reiniciar Aplicativo](../../debugger/media/dbg-tour-restart.png "RestartApp") na barra de ferramentas Depurar (**Ctrl** + **Shift** + **F5**).

Ao pressionar **Reiniciar**, você economiza tempo em comparação com a opção de parar o aplicativo e reiniciar o depurador. O depurador é pausado no primeiro ponto de interrupção que é encontrado pela execução do código.

O depurador para novamente no ponto de interrupção definido por você no método `shape.Draw()`.

## <a name="inspect-variables-with-data-tips"></a>Inspecionar variáveis com dicas de dados

Os recursos que permitem que você inspecione variáveis são uns dos mais úteis do depurador e há diferentes maneiras de fazer isso. Muitas vezes, ao tentar depurar um problema, você tenta descobrir se as variáveis estão armazenando os valores que elas deveriam conter em um momento específico.

1. Durante a pausa no método `shape.Draw()`, passe o mouse sobre o objeto `shapes` e veja o valor da propriedade padrão dele, ou seja, a propriedade `Count`.

1. Expanda o objeto `shapes` para ver todas as suas propriedades, como o primeiro índice da matriz `[0]`, que tem um valor de `Rectangle`.

     ![Exibir uma dica de dados](../visual-basic/media/get-started-data-tip-vb.png "Exibir uma dica de dados")

    Você pode expandir ainda mais os objetos para exibir suas propriedades, como a propriedade `Height` do retângulo.

    Muitas vezes, durante a depuração, queremos uma maneira rápida de verificar valores de propriedade em objetos e as dicas de dados são uma ótima maneira de fazer isso.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspecionar variáveis com as janelas Autos e Locais

1. Examine a janela **Autos** na parte inferior do editor de códigos.

     ![Inspecionar variáveis na janela Autos](../visual-basic/media/get-started-autos-window-vb.png "Janela Autos")

    Na janela **Autos**, veja as variáveis e seus valores atuais. A janela **Autos** mostra todas as variáveis usadas na linha atual ou a linha anterior (verifique a documentação para saber o comportamento específico a uma linguagem).

2. Em seguida, examine a janela **Locais**, em uma guia ao lado da janela **Autos**.

    A janela **Locais** mostra as variáveis que estão no [escopo](https://www.wikipedia.org/wiki/Scope_(computer_science)) atual, ou seja, o contexto de execução atual.

## <a name="set-a-watch"></a>Definir uma inspeção

1. Na janela principal do editor de códigos, clique com o botão direito do mouse no objeto `shapes` e escolha **Adicionar Inspeção**.

    A janela **Inspeção** é aberta na parte inferior do editor de códigos. Você pode usar uma janela **Inspeção** para especificar uma variável (ou uma expressão) que deseja acompanhar.

    Agora, há uma inspeção definida no objeto `shapes` e você pode ver seu valor sendo alterado, conforme percorre o depurador. Ao contrário das outras janelas de variáveis, a janela **Inspeção** sempre mostra as variáveis que você está inspecionando (eles ficam esmaecidas quando estão fora do escopo).

## <a name="examine-the-call-stack"></a>Examinar a pilha de chamadas

1. Durante a pausa no loop `For Each`, clique na janela **Pilha de Chamadas** que fica aberta por padrão no painel inferior direito.

2. Pressione **F11** algumas vezes até que o depurador seja colocado em pausa no método `MyBase.Draw` da classe `Rectangle` no editor de códigos. Examine a janela **Pilha de Chamadas**.

    ![Examinar a pilha de chamadas](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    A janela **Pilha de Chamadas** mostra a ordem em que os métodos e as funções são chamados. A linha superior mostra a função atual (o método `Rectangle.Draw` neste aplicativo). A segunda linha mostra que `Rectangle.Draw` foi chamado por meio da função `Main` e assim por diante.

   > [!NOTE]
   > A janela **Pilha de Chamadas** é semelhante à perspectiva de Depuração em alguns IDEs, como o Eclipse.

    A pilha de chamadas é uma boa maneira de examinar e entender o fluxo de execução de um aplicativo.

    Você pode clicar duas vezes em uma linha de código para examinar esse código-fonte. Isso também altera o escopo atual que está sendo inspecionado pelo depurador. Essa ação não avança o depurador.

    Você também pode usar os menus acessados ao clicar com o botão direito do mouse na janela **Pilha de Chamadas** para fazer outras coisas. Por exemplo, você pode inserir pontos de interrupção em funções especificadas, avançar o depurador usando **Executar até o Cursor** e examinar o código-fonte. Para obter mais informações, confira [Como: Examinar a pilha de chamadas](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Alterar o fluxo de execução

1. Com o depurador em pausa na chamada de método `MyBase.Draw` da classe `Rectangle`, use o mouse para segurar a seta amarela (o ponteiro de execução) à esquerda e movê-la uma linha para cima, até a chamada de método `Console.WriteLine`.

1. Pressione **F11**.

    O depurador executa novamente o método `Console.WriteLine` (você vê uma saída duplicada na saída da janela do console).

    Alterando o fluxo de execução, você pode fazer coisas como testar caminhos de execução de código diferentes ou executar novamente o código sem reiniciar o depurador.

    > [!WARNING]
    > Geralmente, você precisa ter cuidado com esse recurso. Um aviso é exibido na dica de ferramenta. Outros avisos também podem ser exibidos. Ao mover o ponteiro não é possível reverter o aplicativo para um estado anterior.

1. Pressione **F5** para continuar a execução do aplicativo.

    Parabéns por concluir este tutorial.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como iniciar o depurador, percorrer o código e inspecionar variáveis. Talvez você queira obter uma visão geral dos recursos do depurador, com links para mais informações.

> [!div class="nextstepaction"]
> [Introdução ao depurador](../../debugger/debugger-feature-tour.md)
