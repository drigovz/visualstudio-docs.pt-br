---
title: Navegar por uma sessão de depuração (XAML e C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8d24f01f7882e8c760918119a03a1c489c727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156726"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Navegar por uma sessão de depuração no Visual Studio (XAML e C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este guia de início rápido demonstra como navegar nas sessões de depuração do Visual Studio e como exibir e alterar o estado do programa em uma sessão.

 Este início rápido é para desenvolvedores que são novos na depuração com o Visual Studio e para desenvolvedores que desejam saber mais sobre como navegar em uma sessão de depuração do Visual Studio. Ele não ensina a arte de depurar a si próprio. Os métodos no código de exemplo são projetados apenas para demonstrar os procedimentos de depuração descritos neste tópico. Os métodos não empregam práticas recomendadas de design de aplicativo ou função. Na verdade, você descobrirá rapidamente que os métodos e o próprio aplicativo não fazem muito nada.

 As seções desse início rápido foram projetadas para ser tão independentes quanto possível, para que você possa ignorar qualquer seção que inclua informações com as quais você já esteja familiarizado. Você também não precisa criar um aplicativo de exemplo; no entanto, recomendamos isso e tornamos o processo o mais fácil possível.

 **Atalhos de teclado do depurador.** A navegação do depurador do Visual Studio é otimizada para o mouse e o teclado. Muitas das etapas neste tópico incluem o acelerador de teclado ou a tecla de atalho em um comentário entre parênteses. Por exemplo, (teclado: F5) indica que pressionar a tecla F5 inicia ou continua a execução do depurador.

## <a name="in-this-topic"></a>Neste tópico
 Você pode aprender como:

- [Criar o aplicativo de exemplo](#BKMK_CreateTheApplication)

- [Definir e executar para um ponto de interrupção, entrar em um método e examinar os dados do programa](#BKMK_StepInto)

- [Percorrer, acima e fora de métodos](#BKMK_StepIntoOverOut)

- [Definir um ponto de interrupção condicional, executar até o cursor e visualizar uma variável](#BKMK_ConditionCursorVisualize)

- [Editar e continuar, recuperar de uma exceção](#BKMK_EditContinueRecoverExceptions)

## <a name="create-the-sample-app"></a><a name="BKMK_CreateTheApplication"></a> Criar o aplicativo de exemplo
 A depuração é sobre o código, portanto, o aplicativo de exemplo usa a estrutura do aplicativo da Windows Store somente para criar um arquivo de origem no qual você pode ver como a navegação de uma sessão de depuração funciona e como examinar e alterar o estado do programa. Todo o código que você chamará será chamado do construtor da página principal; nenhum controle é adicionado e nenhum evento é manipulado.

 **Crie um aplicativo padrão da Windows Store em C#.** Abra o Visual Studio. Na home page, escolha o link **novo projeto** . Na caixa de diálogo novo projeto, escolha **Visual C#** na lista **instalado** e, em seguida, escolha **Windows Store**. Na lista de modelos de projeto, escolha **aplicativo**. O Visual Studio cria uma nova solução e um novo projeto e exibe o designer MainPage. XAML e o editor de código XAML.

 **Abra o arquivo de origem MainPage.xaml.cs.** Clique com o botão direito do mouse em qualquer lugar no editor XAML e escolha **Exibir código**. O arquivo code-behind MainPage.xaml.cs é exibido. Observe que apenas um método, o `MainPage()` Construtor, está listado no arquivo.

 **Substitua o Construtor MainPage pelo código de exemplo.** Exclua o método MainPage (). Siga este link: [código de exemplo de navegação do depurador (XAML e C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md)e, em seguida, copie o código listado na seção C# para a área de transferência. (Escolha **voltar** no navegador ou no Visualizador da ajuda para retornar a esta página de início rápido.) No editor do Visual Studio, Cole o código no `partial class MainPage` bloco. Escolha CTRL + s para salvar o arquivo.

 {1&gt;Agora você pode acompanhar os exemplos neste tópico.&lt;1}

## <a name="set-and-run-to-a-breakpoint-step-into-a-method-and-examine-program-data"></a><a name="BKMK_StepInto"></a> Definir e executar para um ponto de interrupção, entrar em um método e examinar os dados do programa
 A maneira mais comum de iniciar uma sessão de depuração é escolher **Iniciar Depuração** no menu **depurar** (teclado: F5). A execução começa e continua até que um ponto de interrupção seja atingido, você suspende a execução manualmente, uma exceção ocorre ou o aplicativo termina.

 Quando a execução é suspensa no depurador, você pode exibir o valor de uma variável ativa em uma dica de dados passando o mouse sobre a variável. Você também pode abrir as janelas locais e automáticas para ver as listas das variáveis ativas e seus valores atuais. A adição de uma ou mais variáveis a uma janela de inspeção permite que você se concentre no valor das variáveis à medida que o aplicativo continua a execução.

 Depois de suspender a execução do aplicativo (que também é chamado de quebra no depurador), você controla a maneira como o restante do código do programa é executado. Você pode continuar linha por linha, movendo de uma chamada de método para o próprio método ou pode executar um método chamado em uma única etapa. Esses procedimentos são chamados percorrendo o aplicativo. Você também pode retomar a execução padrão do aplicativo, executando até o próximo ponto de interrupção definido ou até a linha em que você posicionou o cursor. Você pode parar a sessão de depuração a qualquer momento. O depurador foi projetado para executar as operações de limpeza necessárias e sair da execução.

### <a name="example-1"></a>Exemplo 1
 Neste exemplo, você definirá um ponto de interrupção no Construtor MainPage do arquivo MainPage.xaml.cs, entrará no primeiro método, exibirá valores de variáveis e, em seguida, interromperá a depuração.

 **Definir um ponto de interrupção.** Defina um ponto de interrupção na instrução `methodTrack = "Main Page";` no Construtor MainPage. Escolha a linha na medianiz sombreada do editor de código-fonte (teclado: Posicione o cursor na linha e escolha a tecla F9).

 ![Intervir](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 O ícone de ponto de interrupção aparece na medianiz.

 **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: F5).

 O aplicativo começa a ser executado e suspende a execução imediatamente antes da instrução na qual você define o ponto de interrupção. O ícone de linha atual na medianiz identifica seu local e a instrução atual é realçada.

 ![Definir um ponto de interrupção](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Agora você está no controle da execução do aplicativo e pode examinar o estado do programa ao percorrer as instruções do programa.

 **Passe para o método.** No menu **depurar** , escolha **etapa em** (teclado: F11).

 ![Linha atual](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Observe que o depurador passa para a próxima linha, que é uma chamada para o método example1. Escolha Entrar novamente. O depurador passa para o ponto de entrada do método example1. Isso indica que o método foi carregado na pilha de chamadas e que a memória para variáveis locais foi alocada.

 {1&gt;Quando você entra em uma linha de código, o depurador executa uma das seguintes ações:&lt;1}

- {1&gt;Se a próxima instrução não for uma chamada para uma função em sua solução, o depurador executará a instrução, irá para a próxima instrução e suspenderá a execução.&lt;1}

- Se a instrução for uma chamada para uma função em sua solução, o depurador passará para o ponto de entrada da função chamada e, em seguida, suspenderá a execução.

  Continue a entrar nas instruções de example1 até atingir o ponto de saída. O depurador realça a chave de fechamento do método.

  **Examine os valores de variáveis em dicas de dados.** Quando você passa o mouse sobre um nome de variável, o nome, o valor e o tipo da variável são exibidos em uma dica de dados.

  ![Dica de dados do depurador](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Passe o mouse sobre a variável `a` . Observe o nome, o valor e o tipo de dados. Passe o mouse sobre a variável `methodTrack` . Novamente, observe o nome, o valor e o tipo de dados.

  **Examine os valores de variáveis na janela locais.** No menu **depurar** , aponte para **Windows**e escolha **locais**. (Teclado: Alt+4).

  ![Janela locais](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  O Windows local é uma exibição de árvore dos parâmetros e das variáveis da função. As propriedades de uma variável de objeto são nós filho do próprio objeto. A `this` variável é um parâmetro oculto em cada método de objeto que representa o próprio objeto. Nesse caso, representa a classe MainPage. Como `methodTrack` é um membro da classe MainPage, seu valor e o tipo de dados são listados em uma linha abaixo `this` . Expanda o `this` nó para exibir as `methodTrack` informações.

  **Adicione uma inspeção para a variável methodTrack.** A `methodWatch` variável é usada em todo este início rápido para mostrar os métodos chamados nos exemplos. Para facilitar a exibição do valor da variável, adicione-o a uma janela de inspeção. Clique com o botão direito do mouse no nome da variável na janela locais e escolha **Adicionar inspeção**.

  ![janela Inspeção](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  Você pode inspecionar diversas variáveis em uma janela Inspeção. Os valores das variáveis observadas, como valores nas janelas locais e de dica de dados, são atualizados sempre que a execução é suspensa. Você também pode adicionar variáveis à janela Watch a partir do editor de código. Selecione a variável a ser observada, clique com o botão direito do mouse e escolha **Adicionar inspeção**.

## <a name="step-into-over-and-out-of-methods"></a><a name="BKMK_StepIntoOverOut"></a> Percorrer, acima e fora de métodos
 Em contraste com a depuração em um método chamado por um método pai, a depuração por um método executa o método filho e, em seguida, suspende a execução no método de chamada conforme o pai é retomado. Você pode passar por um método quando estiver familiarizado com a maneira como o método funciona e tem certeza de que sua execução não afetará o problema que você está investigando.

 A depuração em uma linha de código que não contém uma chamada de método executa a linha da mesma forma que a etapa na linha.

 A saída de um método filho continua a execução do método e, em seguida, suspende a execução depois que o método retorna ao seu método de chamada. Você pode sair de uma função longa quando tiver determinado que o restante da função não é significativo.

 {6&gt;Tanto passar sobre quanto sair de uma função executam a função.&lt;6}

 ![Percorrer, acima e fora de métodos](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Exemplo 2
 Neste exemplo, você passará para dentro e para fora dos métodos.

 **Chame o método example2 no Construtor MainPage.** Edite o Construtor MainPage e substitua a linha a seguir `methodTrack = String.Empty;` por `Example2();` .

 ![Chamar o método example2 do método demo](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: F5). O depurador suspende a execução no ponto de interrupção.

 **{2&amp;gt;Passe sobre a linha de código.&amp;lt;2}** No menu **depurar** , escolha **passar sobre** (teclado: F10). O depurador executa a `methodTrack = "MainPage";` instrução da mesma maneira que percorrendo a instrução.

 **Entrar em example2 e Example2_A.** Escolha a tecla F11 para entrar no método de exemplo 2. Continue a entrar nas instruções example2 até chegar à linha `int x = Example2_A();` . Novamente, passe nessa linha para mudar para o ponto de entrada de Example2_A. Continue a entrar em cada instrução de Example2_A até retornar para example2.

 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **{2&amp;gt;Passar sobre uma função.&amp;lt;2}** Observe que a próxima linha em example2, `int y = Example2_A();` é basicamente a mesma que a linha anterior. Você pode passar sobre essa linha com segurança. Escolha a tecla F10 para mover da retomada de example2 para essa segunda chamada para Example2_A. Escolha F10 para passar por esse método. Observe que a `methodTrack` cadeia de caracteres indica que o método de Example2_A foi executado duas vezes. Você também observará que o depurador se move imediatamente para a próxima linha. Ele não suspende a execução no ponto em que o example2 é retomado.

 **{2&amp;gt;Sair de uma função.&amp;lt;2}** Escolha a tecla F11 para entrar em Example2_B método. Observe que Example2_B não é muito diferente da Example2_A. Para sair do método, escolha **sair** no menu **depurar** (teclado: Shift + F11). Observe que a `methodTrack` variável indica que Example2_B foi executado e que o depurador retornou ao ponto em que o example2 é retomado.

 **Pare a depuração.** No menu Depurar, escolha Parar Depuração (atalho do teclado: Shift+F5). Isso encerra a sessão de depuração. 

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_ConditionCursorVisualize"></a> Definir um ponto de interrupção condicional, executar para o cursor e visualizar uma variável
 Um ponto de interrupção condicional Especifica uma condição que faz o depurador suspender a execução. A condição é especificada por uma expressão de código que pode ser avaliada como true ou false. Por exemplo, você pode usar um ponto de interrupção condicional para examinar o estado do programa em um método chamado com frequência somente quando uma variável atingir um determinado valor.

 A execução do cursor é como definir um ponto de interrupção único. Quando a execução for suspensa, você poderá selecionar uma linha na origem e retomar a execução até que a linha selecionada seja atingida. Por exemplo, você pode estar percorrendo um loop em um método e determinar que o código no loop está sendo executado corretamente. Em vez de percorrer cada iteração do loop, você pode executar o cursor posicionado após a execução do loop.

 Às vezes, é difícil exibir um valor de variável na linha de dica de dados ou janela variável. O depurador pode exibir cadeias de caracteres, HTML e Xml em um visualizador de texto que apresente uma exibição formatada do valor em uma janela rolável. 

### <a name="example-3"></a>Exemplo 3:
 Neste exemplo, você deve definir um ponto de interrupção condicional para parar em uma iteração específica de um loop e então executar até o cursor que está posicionado após o loop. Você também pode exibir o valor de uma variável em um visualizador de texto.

 **Chame o método Example3 no Construtor MainPage.** Edite o Construtor MainPage e substitua a linha seguinte `methodTrack = String.Empty;` pela linha `Example3();` .

 ![Chamar Example3 a partir do método demo](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: F5). O depurador suspende a execução no ponto de interrupção no método MainPage.

 **Passe para o método Example3.** Escolha **entrar** no menu **depurar** (teclado: F11) para mover para o ponto de entrada do método Example3. Continue a depuração no método até que você tenha iterado um ou dois loops do `for` bloco. Observe que levaria muito tempo para percorrer todas as 1.000 iterações.

 **{2&amp;gt;Defina um ponto de interrupção condicional.&amp;lt;2}** Na medianiz à esquerda da janela de código, clique com o botão direito do mouse na linha `x += i;` e escolha **condição**. Escolha a caixa de seleção **condição** e digite `i == 500;` na caixa de texto. Escolha a opção **é verdadeiro** e escolha **OK**. O ponto de interrupção permite que você verifique o valor na iteração 500th do `for` loop.

 ![Caixa de diálogo condição do ponto de interrupção](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Você pode identificar um ícone de ponto de interrupção condicional pela sua cruz branca.

 ![Ponto de interrupção condicional](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** No menu Depurar, escolha Continuar (teclado: F5). Na janela locais, confirme se o valor atual de `i` é 500. Observe que a variável `s` é representada como uma única linha e é muito maior do que a janela.

 **Visual uma variável de cadeia de caracteres.** Clique no ícone de lupa na coluna **valor** do `s` .

 A janela Visualizador de texto é exibida e o valor da cadeia de caracteres é apresentado como uma cadeia de caracteres de várias linhas.

 **{2&amp;gt;Execute até o cursor.&amp;lt;2}** Clique com o botão direito do mouse na linha `methodTrack += "->Example3";` e escolha **executar até o cursor** (teclado: mover o cursor para a linha; Ctrl + F10). O depurador conclui as iterações do loop e então suspende a execução na linha.

 **Pare a depuração.** No menu Depurar, escolha Parar Depuração (atalho do teclado: Shift+F5). Isso encerra a sessão de depuração. 

## <a name="edit-and-continue-recover-from-an-exception"></a><a name="BKMK_EditContinueRecoverExceptions"></a> Editar e continuar, recuperar de uma exceção
 Em algumas circunstâncias, quando você divide o código no depurador do Visual Studio, você tem a oportunidade de alterar o valor de variáveis e até mesmo as lógicas de instruções. Essa funcionalidade é chamada editar e continuar.

 Editar e continuar pode ser especialmente útil ao interromper uma exceção. Em vez de ter que parar e reiniciar a depuração de um procedimento longo e envolvido para evitar a exceção, você pode "desenrolar" a exceção para mover a execução até o ponto imediatamente antes que a exceção ocorra e, em seguida, alterar a variável ou a instrução incorreta e continuar com a sessão de depuração atual no estado que não gera uma exceção.

 Embora você possa usar editar e continuar em uma ampla variedade de situações, as condições específicas que não dão suporte a editar e continuar são difíceis de especificar, pois as condições dependem da linguagem de programação, do estado atual da pilha de programas e da capacidade do depurador de alterar o estado sem corromper o processo. A melhor maneira de determinar se uma alteração de edição tem suporte é apenas tentar; o depurador permite que você saiba imediatamente se não há suporte para a alteração.

### <a name="example-4"></a>Exemplo 4
 Neste exemplo, você executa o depurador para uma exceção, rebobina a exceção, corrige a lógica do método e, em seguida, altera o valor de uma variável para que você possa continuar executando o método.

 **Chame o método Example4 no Construtor MainPage.** Edite o Construtor MainPage () e substitua a linha a seguir `methodTrack = String.Empty;` pela linha `Example4();` .

 ![Chamar Example4 a partir do método demo](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Execute para a exceção.** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: F5). Pressione F5 novamente para retomar a execução. O depurador suspende a execução na exceção no método Example4 e exibe uma caixa de diálogo de exceção.

 ![Caixa de diálogo de exceção](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Altere a lógica do programa.** É óbvio que o erro está na `if` condição: o valor de `x` deve ser alterado quando é `x` igual a 0; não quando `x` não é igual a zero. Escolha **interromper** para corrigir a lógica do método. Quando você tenta editar a linha, outra caixa de diálogo é exibida.

 ![Caixa de diálogo Editar e continuar](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 Escolha **Editar** e, em seguida, altere a linha `if (x != 0)` para `if (x == 0)` . O depurador mantém as alterações na lógica do programa para o arquivo de origem.

 **Altere o valor da variável.** Examine o valor de `x` em uma dica de dados ou na janela locais. Ele ainda é 0 (zero). Se você tentar executar a instrução que causou a exceção original, ela será novamente emitida novamente. Você pode alterar o valor de `x` . Na janela locais, clique duas vezes na coluna **valor** da linha **x** . Altere o valor de 0 para 1.

 ![Editar um valor na janela locais](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Escolha a tecla F11 para entrar na instrução que gerou uma exceção anteriormente. Observe que a linha é executada sem erro. Escolha F11 novamente.

 **Pare a depuração.** No menu **depurar** , escolha **parar depuração** (teclado: Shift + F5). Isso encerra a sessão de depuração. 

## <a name="see-also"></a>Consulte Também
 [Iniciar uma sessão de depuração (VB, C#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [disparar eventos de suspensão, retomada e de segundo plano para a Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
