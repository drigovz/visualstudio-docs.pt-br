---
title: Controlar a execução de um aplicativo da loja na sessão de depuração para aplicativos da Windows Store (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9238bd4f42291af23a1279c9caa83f1039c8f249
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838688"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Controlar a execução de um aplicativo da Store em uma sessão de depuração do Visual Studio para Aplicativos da Windows Store (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este início rápido demonstra como navegar no depurador do Visual Studio e como exibir o estado do programa em uma sessão.

 Este início rápido é para desenvolvedores que são novos na depuração com o Visual Studio e para desenvolvedores que desejam saber mais sobre como navegar em uma sessão de depuração do Visual Studio. Ele não ensina a arte de depurar a si próprio. As funções no código de exemplo destinam-se somente a demonstrar os procedimentos de depuração descritos neste tópico. As funções não utilizam as práticas recomendadas de design de aplicativo ou função. Na verdade, você descobrirá rapidamente que as funções e o próprio aplicativo não fazem muito nada.

 As seções desse início rápido foram projetadas para ser tão independentes quanto possível, para que você possa ignorar qualquer seção que inclua informações com as quais você já esteja familiarizado. Você também não precisa criar um aplicativo de exemplo. No entanto, recomendamos isso e tornamos o processo o mais fácil possível.

 **Atalhos de teclado do depurador.** A navegação no depurador do Visual Studio é otimizada tanto para mouse quanto para teclado. Muitas das etapas neste tópico incluem o acelerador de teclado ou a tecla de atalho em um comentário entre parênteses. Por exemplo, (teclado: F5) indica que pressionar a tecla F5 inicia ou continua a execução do depurador.

> [!NOTE]
> **O padrão de módulo**
>
> Os aplicativos da Windows Store geralmente usam o *padrão de módulo* JavaScript para encapsular dados e funções em uma página. O padrão Módulo usa um fechamento único, autoexecutado e anônimo para manter a funcionalidade de página separada do namespace global. Neste tópico, chamamos essa função do *módulo*.

## <a name="in-this-topic"></a>Neste tópico
 Você pode aprender como:

 [Criar o aplicativo de exemplo](#BKMK_Create_the_sample_app)

 [Definir e executar até um ponto de interrupção, entrar em uma função e examinar os dados de programa](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)

 [Entrar, passar sobre e sair de funções](#BKMK_Step_into__over__and_out_of_functions)

 [Definir um ponto de interrupção condicional, executar até o cursor e visualizar uma variável](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)

 [Exibir dados da variável na janela Locais](#BKMK_View_variable_data_in_the_Locals_window)

- [{1&amp;gt;{2&amp;gt;Exibir dados da variável e a cadeia de protótipos de um objeto&amp;lt;2}&amp;lt;1}](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)

- [{1&amp;gt;{2&amp;gt;Examinar dados da cadeia do escopo&amp;lt;2}&amp;lt;1}](#BKMK_Examine_scope_chain_data)

  [{1&amp;gt;{2&amp;gt;Navegue até o código usando a janela Pilha de Chamadas&amp;lt;2}&amp;lt;1}](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)

## <a name="create-the-sample-app"></a><a name="BKMK_Create_the_sample_app"></a> Criar o aplicativo de exemplo
 A depuração é sobre o código, portanto, o aplicativo de exemplo usa a estrutura do aplicativo da Windows Store somente para criar um arquivo de origem no qual você pode ver como a navegação de uma sessão de depuração funciona e como examinar o estado do programa. Todo o código que você vai invocar é chamado por meio da função `module` do arquivo default. js. Nenhum controle é adicionado e nenhum evento é tratado.

1. **{2&amp;gt;Crie um aplicativo JavaScript da Windows Store em branco.&amp;lt;2}** Abra o Visual Studio. Na home page, escolha o link **novo projeto** . Na caixa de diálogo **novo projeto** , escolha **JavaScript** na lista **instalado** e, em seguida, escolha **Windows Store**. Na lista de modelos de projeto, escolha **aplicativo em branco**. Visual Studio cria uma nova solução e projeto e exibe o arquivo default.htm no editor de códigos.

    {10&gt;Observe os arquivos de script que são carregados para a página. &lt;10}

   - Os `base.js` `ui.js` arquivos e criam a **biblioteca do Windows para JavaScript**. A Biblioteca do Windows para JavaScript é um conjunto de arquivos em JavaScript e CSS que tornam mais fácil criar aplicativos da Windows Store usando JavaScript. Use-a junto com HTML, CSS e o Tempo de Execução do Windows para criar seu aplicativo.

   - Seu código começa no `default.js`  arquivo.

2. **{2&amp;gt;Abra o arquivo de origem default.js.&amp;lt;2}** No Gerenciador de Soluções, abra o nó **js** e escolha `default.js` .

3. **{2&amp;gt;Substitua o conteúdo da página com o código de exemplo.&amp;lt;2}** Exclua todo o conteúdo do `default.js` arquivo. Siga este link: [código de exemplo de navegação do depurador (JavaScript)](../debugger/debugger-navigation-sample-code-javascript.md)e, em seguida, copie o código listado na seção JavaScript para a área de transferência. (Escolha **voltar** no navegador ou no Visualizador da ajuda para retornar a esta página de início rápido.) No editor do Visual Studio, Cole o código no agora vazio `default.js` . Escolha **Ctrl + S** para salvar o arquivo.

   {1&gt;Agora você pode acompanhar os exemplos neste tópico.&lt;1}

## <a name="set-and-run-to-a-breakpoint-step-into-a-function-and-examine-program-data"></a><a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Definir e executar para um ponto de interrupção, entrar em uma função e examinar os dados do programa
 A maneira mais comum de iniciar uma sessão de depuração é escolher **Iniciar Depuração** no menu **depurar** (teclado: F5). O aplicativo é iniciado e continua sendo executado até que um ponto de interrupção seja atingido, você suspende a execução manualmente, uma exceção ocorre ou o aplicativo termina.

 Quando a execução é suspensa no depurador, você pode exibir o valor de uma variável ativa em uma dica de dados pausando o mouse na variável.

 Depois de suspender a execução do aplicativo (que também é chamado de invadir o depurador), você controla a maneira como o restante do código do programa é executado. Você pode continuar a linha por linha, movendo de uma chamada de função para a função em si, ou pode executar uma função chamada em uma única etapa. Esses procedimentos são chamados percorrendo o aplicativo. Você também pode retomar a execução padrão do aplicativo, executando até o próximo ponto de interrupção definido ou até a linha em que você posicionou o cursor. Você pode parar a sessão de depuração a qualquer momento. O depurador foi projetado para executar as operações de limpeza necessárias e sair da execução.

### <a name="example-1"></a><a name="BKMK_Example_1"></a> Exemplo 1
 Neste exemplo, você define um ponto de interrupção no corpo da `module` função `default.js` como chama o primeiro de nossas instruções de usuário. Em seguida, você entra na função, exibe valores de variáveis em dicas de dados do depurador e então interrompe a depuração.

1. **Definir um ponto de interrupção.** Defina um ponto de interrupção na instrução `callTrack = "module function";` que ocorre logo após a chamada para `app.start()` . Escolha a linha na medianiz sombreada do editor de código-fonte (teclado: Posicione o cursor na linha e escolha a tecla **F9** ).

    ![Definir um ponto de interrupção em example1](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")

    O ícone de ponto de interrupção aparece na medianiz.

2. **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: F5).

    O aplicativo começa a ser executado e suspende a execução imediatamente antes da instrução na qual você define o ponto de interrupção. O ícone de linha atual na medianiz identifica seu local e a instrução atual é realçada.

    ![Executar até ponto de interrupção](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")

    Agora você está no controle da execução do aplicativo e pode examinar o estado do programa ao percorrer as instruções do programa.

3. **{2&amp;gt;Entrar na função.&amp;lt;2}** No menu **depurar** , escolha **etapa em** (teclado: **F11**).

    ![Entrar em uma linha de código](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")

    Observe que o depurador passa para a próxima linha, que é uma chamada para a `example1` função. Escolha **entrar** novamente. O depurador vai para a primeira linha de código da função `example1`. A linha realçada não foi sido executada, mas a função foi carregada na pilha de chamadas e a memória para variáveis locais foi alocada.

4. {1&gt;Quando você entra em uma linha de código, o depurador executa uma das seguintes ações:&lt;1}

   - {1&gt;Se a próxima instrução não for uma chamada para uma função em sua solução, o depurador executará a instrução, irá para a próxima instrução e suspenderá a execução.&lt;1}

   - {1&gt;Se a instrução for uma chamada para uma função em sua solução, o depurador irá para a primeira linha da função chamada e então suspenderá a execução.&lt;1}

     Continue a entrar nas instruções de `example1` até que você tenha atingido o ponto de saída. O depurador realça a chave de fechamento da função.

5. **{2&amp;gt;Exiba os valores de variáveis em dicas de dados.&amp;lt;2}** Continue a entrar nas instruções de `example1` até que você tenha atingido o ponto de saída. O depurador realça a chave de fechamento da função. Quando você pausa o mouse em um nome de variável, o nome e o valor da variável são exibidos em uma dica de dados.

    ![Exibir valores de variáveis na dica de dados](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")

6. **{2&amp;gt;Adicione uma inspeção para a variável callTrack.&amp;lt;2}** A `callTrack` variável é usada em todo este início rápido para mostrar as funções chamadas nos exemplos. Para facilitar a exibição do valor da variável, adicione-o uma janela Inspeção. Selecione o nome da variável no editor e, em seguida, escolha **Adicionar inspeção** no menu de atalho.

    ![Observar uma variável](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")

    Você pode inspecionar diversas variáveis em uma janela Inspeção. Os valores de variáveis inspecionadas, como valores em janelas de dica de dados, são atualizados sempre que a execução é suspensa. As variáveis inspecionadas são salvas nas sessões de depuração.

7. **Pare a depuração.** No menu **depurar** , escolha **parar depuração** (teclado: **Shift + F5**). Isso encerra a sessão de depuração. 

## <a name="step-into-over-and-out-of-functions"></a><a name="BKMK_Step_into__over__and_out_of_functions"></a> Percorrer, acima e fora de funções
 Em contraste a entrar em uma função chamada por uma função pai, passar sobre uma função executa a função filha e, em seguida, suspende a execução da função de chamada conforme a função pai é retomada. Você pode entrar em uma função quando estiver familiarizado com a maneira como a função funciona e tiver certeza de que sua execução não afetará o problema que você está investigando.

 A depuração em uma linha de código que não contém uma chamada de função executa a linha da mesma forma que a etapa na linha.

 A saída de uma função filho continua a execução da função e suspende a execução depois que a função retorna à sua função de chamada. Você pode sair de uma função longa quando tiver determinado que o restante da função não é significativo.

 {6&gt;Tanto passar sobre quanto sair de uma função executam a função.&lt;6}

 ![Percorrer, acima e fora de métodos](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a><a name="BKMK_Example_2"></a> Exemplo 2
 {1&gt;Neste exemplo, você pode entrar, passar sobre e sair de funções. &lt;1}

1. **{2&amp;gt;Chame a função example2 na função de módulo.&amp;lt;2}** Edite a `module` função e substitua a linha a seguir `var callTrack = "module function"` por `example2();` .

     ![Chamar a função example2](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")

2. **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: F5). O depurador suspende a execução no ponto de interrupção.

3. **{2&amp;gt;Passe sobre a linha de código.&amp;lt;2}** No menu **depurar** , escolha **passar sobre** (teclado: F10). O depurador executa a `var callTrack = "module function"` instrução da mesma maneira que percorrendo a instrução.

4. **{2&amp;gt;Entrar em example2 e example2_a.&amp;lt;2}** Escolha a tecla **F11** para entrar na `example2` função. Continue a entrar nas `example2` instruções até chegar à linha `var x = example2_a();` . Novamente, passe nessa linha para mover para o ponto de entrada de `example2_a` . Continue a entrar em cada instrução do `example2_a` até retornar ao `example2` .

     ![Passar por uma função](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")

5. **{2&amp;gt;Passar sobre uma função.&amp;lt;2}** Observe que a próxima linha no `example2` , `var y = example2_a();` é basicamente igual à linha anterior. Você pode passar sobre essa linha com segurança. Escolha a tecla **F10** para mover da retomada de `example2` para essa segunda chamada para `example2_a` . Observe que a `callTrack` cadeia de caracteres indica que a `example2_a` função foi executada duas vezes.

6. **{2&amp;gt;Sair de uma função.&amp;lt;2}** Escolha a tecla **F11** para entrar na `example2_b` função. Observe que `example2_b` não é muito diferente de `example2_a`. Para sair da função, escolha **sair** no menu **depurar** (teclado: **Shift + F11**). Observe que a `callTrack` variável indica que `example2_b` foi executada e que o depurador retornou ao ponto em que o é `example2` retomado.

7. **Pare a depuração.** No menu **depurar** , escolha **parar depuração** (teclado: **Shift + F5**). Isso encerra a sessão de depuração. 

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Definir um ponto de interrupção condicional, executar para o cursor e visualizar uma variável
 Um ponto de interrupção condicional Especifica uma condição que faz o depurador suspender a execução. A condição é especificada por uma expressão de código que pode ser avaliada como true ou false. Por exemplo, você pode usar um ponto de interrupção condicional para examinar o estado do programa em uma função chamada com frequência somente quando uma variável atingir um determinado valor.

 A execução do cursor é como definir um ponto de interrupção único. Quando a execução for suspensa, você poderá selecionar uma linha na origem e retomar a execução até que a linha selecionada seja atingida. Por exemplo, você pode percorrer um loop em uma função e determinar que o código no loop está sendo executado corretamente. Em vez de percorrer cada iteração do loop, você pode executar o cursor posicionado após a execução do loop.

 Às vezes, é difícil exibir um valor de variável na linha de uma dica de dados ou em outra janela de dados. O depurador pode exibir cadeias de caracteres, HTML e Xml em um visualizador de texto que apresente uma exibição formatada do valor em uma janela rolável. 

### <a name="example-3"></a><a name="BKMK_Example_3"></a> Exemplo 3
 Neste exemplo, você deve definir um ponto de interrupção condicional para parar em uma iteração específica de um loop e então executar até o cursor que está posicionado após o loop. Você também pode exibir o valor de uma variável em um visualizador de texto.

1. **{2&amp;gt;Chame a função example3 na função de módulo.&amp;lt;2}** Edite a `module` função e substitua a linha seguinte `var callTrack = "module function";` pela linha `example3();` .

     ![Chamar example3](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")

2. **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: **F5**). O depurador suspende a execução no ponto de interrupção na `module` função.

3. **{2&amp;gt;Entre na função example3.&amp;lt;2}** Escolha **entrar** no menu **depurar** (teclado: **F11**) para mover para o ponto de entrada da `example3` função. Continue percorrendo a função até que você tenha iterado um ou dois loops do `for` bloco. Observe que levaria muito tempo para percorrer todas as 1.000 iterações.

4. **{2&amp;gt;Defina um ponto de interrupção condicional.&amp;lt;2}** Na medianiz à esquerda da janela de código, clique com o botão direito do mouse na linha `s += i.toString() + "\n";` e escolha **condição** no menu de atalho.

     Marque a caixa de seleção **condição** e digite `i == 500;` na caixa de texto. Escolha a opção **é verdadeiro** e escolha **OK**. O ponto de interrupção permite que você verifique o valor na iteração 500th do `for` loop. Você pode identificar um ícone de ponto de interrupção condicional pela sua cruz branca.

     ![Ícone de ponto de interrupção bloquear](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")

5. **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** No menu **depurar** , escolha **continuar** (teclado: **F5**). Pause no `i` para confirmar que o valor atual de `i` é 500. Observe também que a variável `s` é representada como uma única linha e é muito maior do que a janela de dica de dados.

6. **{2&amp;gt;Visualize uma variável de cadeia de caracteres.&amp;lt;2}** Clique no ícone de lupa na dica de dados do `s` .

     A janela Visualizador de texto é exibida e o valor da cadeia de caracteres é apresentado como uma cadeia de caracteres de várias linhas.

     ![Visualizador de texto de depuração](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")

7. **{2&amp;gt;Execute até o cursor.&amp;lt;2}** Selecione a linha `callTrack += "->example3";` e, em seguida, escolha **executar até o cursor** no menu de atalho (teclado: **Ctrl + F10**). O depurador conclui as iterações do loop e então suspende a execução na linha.

8. **Pare a depuração.** No menu **depurar** , escolha **parar depuração** (teclado: **Shift + F5**). Isso encerra a sessão de depuração. 

### <a name="use-run-to-cursor-to-return-to-your-code-and-delete-a-breakpoint"></a><a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Use executar para cursor para retornar ao seu código e excluir um ponto de interrupção
 Executar até o cursor pode ser muito útil quando você tiver entrado em código de biblioteca da Microsoft ou terceiros. Embora percorrer o código de biblioteca possa ser informativo, isso geralmente pode demorar muito. E, em geral, você estará muito mais interessado em seu próprio código. Este exercício mostra como fazer isso.

1. **{2&amp;gt;Defina um ponto de interrupção na chamada app.start.&amp;lt;2}** Na `module` função, defina um ponto de interrupção na linha `app.start()`

2. **{1&amp;gt;{2&amp;gt;Execute até o ponto de interrupção e entre na função de biblioteca.&amp;lt;2}&amp;lt;1}**

     Quando você entrar em `app.start()`, o editor exibirá o código em `base.js`. Entre em mais algumas linhas.

3. **{2&amp;gt;Percorra e saia de funções.&amp;lt;2}** À medida que você passa (**F10**) e sai do código (**Shift + F11**) no `base.js` , pode chegar à conclusão de que examinar a complexidade e o comprimento da função de início não é o que você deseja fazer.

4. **{2&amp;gt;Defina o cursor para seu código e execute até ele.&amp;lt;2}** Volte para o arquivo `default.js` no editor de códigos. Selecione a primeira linha de código após `app.start()` (você não pode executar até um comentário ou uma linha em branco). Escolha **executar até o cursor** no menu de atalho. O depurador continua a execução da função app.start e suspende a execução no ponto de interrupção.

## <a name="view-variable-data-in-the-locals-window"></a><a name="BKMK_View_variable_data_in_the_Locals_window"></a> Exibir dados de variáveis na janela locais
 {1&gt;&lt;1}
  {2&gt;A janela Locais é um modo de exibição de árvore dos parâmetros e variáveis da cadeia do escopo da função em execução no momento. &lt;2}

### <a name="view-variable-data-and-the-prototype-chain-of-an-object"></a><a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Exibir dados de variáveis e a cadeia de protótipo de um objeto

1. **{2&amp;gt;Adicione um objeto de matriz à função do módulo.&amp;lt;2}** Edite a `module` função e substitua a linha seguinte `var callTrack = "module function"` por `var myArray = new Array(1, 2, 3);`

     ![definição de myArray](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")

2. **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: **F5**). O depurador suspende a execução no ponto de interrupção. Entre na linha.

3. **{2&amp;gt;Abre a janela Locais.&amp;lt;2}** No menu **depurar** , aponte para **Windows**e escolha **locais**. (Teclado: Alt+4).

4. **Examinar as variáveis locais na função de módulo** As janelas locais exibem as variáveis da função atualmente em execução (a `module` função) como nós de nível superior da árvore. Quando você insere uma função, o JavaScript cria todas as variáveis e fornece a elas um valor de `undefined` . Funções que são definidas na função têm seu texto como um valor.

     ![Janela locais](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")

5. **{2&amp;gt;Percorra as definições de callTrack e myArray.&amp;lt;2}** Encontre as variáveis callTrack e myArray na janela Locais. Percorra (**F10**) as duas definições e observe que os campos de **valor** e **tipo** são alterados. A janela Locais realça os valores das variáveis que foram alterados desde a última interrupção.

6. **Examinar o objeto myArray** Expanda a `myArray` variável. Cada elemento da matriz é listado no nó **[Prototype]** que contém a hierarquia de herança do `Array` objeto. Expanda esse nó.

     ![Cadeia de protótipos na janela locais](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")

    - O nó **métodos** lista todos os métodos do `Array` objeto.

    - O nó **[Prototype]** contém o protótipo do `Object` objeto do qual `Array` é derivado. os nós **[Prototype]** podem ser recursivos. Cada objeto pai em uma hierarquia de objetos é descrito no nó **[Prototype]** de seu filho.

7. **Pare a depuração.** No menu **depurar** , escolha **parar depuração** (teclado: Shift + F5). Isso encerra a sessão de depuração. 

## <a name="examine-scope-chain-data"></a><a name="BKMK_Examine_scope_chain_data"></a> Examinar dados da cadeia de escopo
 A *cadeia de escopo* de uma função inclui todas as variáveis que estão ativas e acessíveis pela função. Variáveis globais são parte da cadeia de escopo, assim como quaisquer objetos (incluindo funções) definidos na função que define a função atualmente em execução. Por exemplo, a `callTrack` variável que é definida na `module` função de `default.js` pode ser acessada por qualquer função definida na `module` função. Cada escopo é listado separadamente na janela Locais.

- {1&gt;As variáveis da função que está em execução no momento são listadas na parte superior da janela.&lt;1}

- As variáveis de cada escopo de função na cadeia de escopo são listadas em um nó **[escopo]** para a função. As funções de escopo são listadas pela sua ordem na cadeia, da função que define a função atual para a função mais externa da cadeia. 

- O nó **[Globals]** lista os objetos globais que são definidos fora de qualquer função.

  Cadeias de escopo podem ser confusas e são mais bem ilustradas pelo exemplo. No exemplo a seguir, você pode ver como a `module` função cria seu próprio escopo e como você pode criar outro nível de escopo criando um fechamento.

### <a name="example-4"></a><a name="BKMK_Example_4"></a> Exemplo 4

1. **{2&amp;gt;Chame a função example4 da função de módulo.&amp;lt;2}** Edite a `module` função e substitua a linha seguinte `var callTrack = "module function"` pela `example4()` :

     ![Chamar example4](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")

2. **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: **F5**). O depurador suspende a execução no ponto de interrupção.

3. **{2&amp;gt;Abre a janela Locais.&amp;lt;2}** Se necessário, no menu **depurar** , aponte para **Windows**e escolha **locais**. (Teclado: **ALT + 4**). Observe que a janela lista todas as variáveis e funções na `module` função e também contém um nó **[Globals]** .

4. **{2&amp;gt;Examine as variáveis globais.&amp;lt;2}** Expanda o nó **[Globals]** . Os objetos e as variáveis em Global foram definidos pela biblioteca do Windows para JavaScript. Você pode adicionar suas próprias variáveis ao escopo global. 

5. **Entrar em example4 e examinar suas variáveis locais e de escopo** Intervir (teclado: **F11**) a `example4` função. Como `example4` é definido na `module` função, a `module` função se torna o escopo pai. `example4` pode chamar qualquer uma das funções na `module` função e acessar suas variáveis. Expanda o nó **[escopo]** na janela locais e observe que ele contém as mesmas e variáveis da `module` função.

     ![Escopos do método example4](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")

6. **Entrar em example4_a e examinar suas variáveis locais e de escopo** Continue a entrar `example4` e entrar na chamada para `example4_a` . Observe que as variáveis locais agora são de `example4_a` e que o nó **[Scope]** continua a manter as variáveis da `module` função. Embora as variáveis do `example4` estejam ativas, elas não podem ser acessadas pelo `example4_a` e não fazem mais parte da cadeia de escopo.

7. **Entrar em multiplyByA e examinar suas variáveis locais e de escopo** Percorra o restante de `example4_a` e para a linha `var x = multiplyByA(b);` .

     A variável de função foi `multiplyByA` definida para a `multiplyClosure` função que é um *fechamento*. `multiplyClosure` define e retorna uma função interna, `multiplyXby` e captura (fecha-se) seu parâmetro e variável. Em um fechamento, a função interna retornada tem acesso aos dados da função externa e, portanto, cria seu próprio nível de escopo.

     Ao entrar `var x = multiplyByA(b);` , você passa para a `return a * b;` linha na `multiplyXby` função interna.

8. Na janela locais, somente o parâmetro `b` é listado como uma variável local no `multiplyXby` , mas um novo nível de **[escopo]** foi adicionado. Expandindo esse nó, você verá que ele contém os parâmetros, as funções e as variáveis de `multiplyClosure`, incluindo a variável `a` chamada na primeira linha de `multiplyXby`. Uma verificação rápida do segundo nó **[Scope]** revela as variáveis de função de módulo, que são `multiplyXby` acessadas em sua próxima linha.

9. **Pare a depuração.** No menu **depurar** , escolha **parar depuração** (teclado: **Shift + F5**). Isso encerra a sessão de depuração. 

## <a name="navigate-to-code-by-using-the-call-stack-window"></a><a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Navegar até o código usando a janela pilha de chamadas
 A pilha de chamadas é uma estrutura de dados que contém informações sobre as funções que estão em execução no thread atual do aplicativo. Quando você atinge um ponto de interrupção, a janela Pilha de Chamadas exibe uma lista de todas as funções que estão ativas na pilha. A função que está em execução no momento está no topo da lista da janela Pilha de Chamadas. A função que inicia o thread está na parte inferior da lista. As funções entre o topo e a parte inferior mostram o caminho da chamada da função inicial até a função atual.

 Além de mostrar o caminho da chamada até a função em execução no momento, a janela Pilha de Chamadas pode ser usada para navegar para o código no editor de códigos. Essa funcionalidade pode ser valiosa quando você estiver trabalhando com vários arquivos e desejar ir rapidamente para uma função específica.

### <a name="example-5"></a><a name="BKMK_Example_5"></a> Exemplo 5
 {1&gt;Neste exemplo, você deve entrar em um caminho de chamada que contenha cinco funções definidas pelo usuário. &lt;1}

1. **{2&amp;gt;Chame a função example5 na função de módulo.&amp;lt;2}** Edite a `module` função e substitua a linha seguinte `var callTrack = "module function";` pela linha `example5();` .

     ![Chamar example5](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")

2. **{2&amp;gt;Execute até o ponto de interrupção.&amp;lt;2}** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **depurar** (teclado: **F5**). O depurador suspende a execução no ponto de interrupção na função de módulo. 

3. **{2&amp;gt;Abra a janela Pilha de Chamadas.&amp;lt;2}** No menu **depurar** , escolha **Windows**e escolha **pilha de chamadas** (teclado: Alt + 7). Observe que a janela Pilha de Chamadas mostra duas funções: 

    - **Código global** é o ponto de entrada da `module` função na parte inferior da pilha de chamadas.

    - **Função anônima** mostra a linha na `module` função em que a execução é suspensa. Essa é a parte superior da pilha de chamadas.

4. **{2&amp;gt;Entre nas funções para chegar à função example5_d.&amp;lt;2}** Escolha **entrar** no menu **depurar** (teclado: **F11**) para executar as chamadas no caminho de chamada até chegar ao ponto de entrada da função example5_d. Observe que cada vez que uma função chama uma função, o número de linha da função de chamada é salvo e a função chamada é colocada na parte superior da pilha. O número de linha da função de chamada é o ponto em que a função de chamada suspendeu a execução. Uma seta amarela aponta para a função atualmente em execução.

     ![Janela pilha de chamadas](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")

5. **{2&amp;gt;Use a janela Pilha de Chamadas para navegar até o código example5_a e definir um ponto de interrupção.&amp;lt;2}** Na janela pilha de chamadas, selecione o `example5_a` item de lista e, em seguida, escolha **ir para origem** no menu de atalho. O editor de código define o cursor na linha de retorno da função. Defina um ponto de interrupção nessa linha. Observe que a linha de execução atual não é alterada. Somente o cursor do editor foi movido.

6. **{2&amp;gt;Entre em funções e, em seguida, execute até o ponto de interrupção.&amp;lt;2}** Continue a depuração `example5_d` . Observe que, quando você retorna da função, ela é retirada da pilha de chamadas. Pressione **F5** para continuar a execução do programa. Você para no ponto de interrupção criado na etapa anterior.

7. **Pare a depuração.** No menu **depurar** , escolha **parar depuração** (teclado: **Shift + F5**). Isso encerra a sessão de depuração. 

## <a name="see-also"></a>Consulte Também
 [Iniciar uma sessão de depuração (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md) início rápido: início rápido de [navegação do depurador (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [: Depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md) [disparar eventos de suspensão, retomada e segundo plano para a Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
