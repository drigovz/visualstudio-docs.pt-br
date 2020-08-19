---
title: Navegando pelo código com o depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "88608934"
---
# <a name="navigating-through-code-with-the-debugger"></a>Navegar pelo Código com o Depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Familiarize-se com comandos e atalhos para navegar pelo código no depurador e isso fará com que seja mais rápido e fácil localizar e resolver problemas em seu aplicativo. Ao navegar no código no depurador, você pode [inspecionar o estado do seu aplicativo](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) ou saber mais sobre seu fluxo de execução.  
  
## <a name="start-debugging"></a>Iniciar a depuração  
 Geralmente, você inicia uma sessão de depuração usando **F5** (**debug**  /  **Iniciar Depuração**). Esse comando inicia seu aplicativo com o depurador anexado.  
  
 A seta verde também inicia o depurador (o mesmo que **F5**).  
  
 ![Noções básicas do DBG&#95;&#95;iniciar&#95;depuração](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Algumas outras maneiras que você pode iniciar o aplicativo com o depurador anexado incluem **F11** ([etapa no código](#BKMK_Step_into__over__or_out_of_the_code)),  **F10** ([passar pelo código](#BKMK_Step_over_Step_out)) ou usando **executar até o cursor**.  Consulte as outras seções neste tópico para obter informações sobre o que essas opções fazem.  
  
 Quando você depura, a linha amarela mostra o código que será executado em seguida.  
  
 ![DBG&#95;noções básicas&#95;&#95;modo de interrupção](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Durante a depuração, você pode alternar entre comandos como **F5**, **F11** e usar outros recursos descritos neste tópico (como pontos de interrupção) para obter rapidamente o código que você deseja examinar.  
  
 A maioria dos recursos do depurador, como a exibição de valores de variáveis na janela locais ou a avaliação de expressões no janela Inspeção, está disponível somente enquanto o depurador é pausado (também chamado de *modo de interrupção*). Quando o depurador é pausado, o estado do aplicativo é suspenso enquanto as funções, variáveis e objetos permanecem na memória. No modo de interrupção, você pode examinar as posições e os Estados dos elementos para procurar violações ou bugs. Para alguns tipos de projeto, você também pode fazer ajustes no aplicativo enquanto estiver no modo de interrupção.  
  
## <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Entrar no código, linha por linha  
 Para parar em cada linha de código (cada instrução) durante a depuração, use o atalho de teclado **F11** (ou **Debug**  /  **a etapa** de depuração no menu).  
  
> [!TIP]
> Ao executar cada linha de código, você pode passar o mouse sobre variáveis para ver seus valores ou usar as janelas [locais](../debugger/autos-and-locals-windows.md) e [assistir](../debugger/autos-and-locals-windows.md) para ver seus valores alterados.  
  
 Aqui estão alguns detalhes sobre o comportamento da **etapa em**:  
  
- Em uma chamada de função aninhada, a **Depuração Completa** intervém na função aninhada mais profunda. Se você usar **Step Into** em uma chamada como `Func1(Func2())` , o depurador percorre a função `Func2` .  
  
- O depurador avança realmente com as instruções de código em vez de linhas físicas. Por exemplo, uma cláusula `if` pode ser gravada em uma linha:  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   Quando você entra nessa linha, o depurador trata a condição como uma etapa e a consequência como outra (nesse exemplo, a condição é verdadeira.)  
  
  Para rastrear visualmente a pilha de chamadas durante a depuração de funções, consulte [métodos de mapeamento na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="step-through-code-skipping-functions"></a><a name="BKMK_Step_over_Step_out"></a> Percorrer o código, ignorando funções  
 Ao executar o código no depurador, muitas vezes você perceberá que não precisa ver o que acontece em uma função específica (você não se preocupa com isso ou sabe que ele funciona, como um código de biblioteca bem testado). Use estes comandos para ignorar o código (as funções ainda são executadas, é claro, mas o depurador as ignora).  
  
|Comando do teclado|Menu Comando|Descrição|  
|----------------------|------------------|-----------------|  
|**F10**|**Contornar**|Se a linha atual contiver uma chamada de função, **Step Over** executará o código e suspenderá a execução na primeira linha de código depois que a função chamada retornar.|  
|**Shift + F11**|**Sair**|O **Step Out** continua executando o código e suspende a execução quando a função atual retorna (o depurador ignora a função atual).|  
  
> [!TIP]
> Se você precisar localizar o ponto de entrada em seu aplicativo, comece com **F10** ou **F11**. Esses comandos são geralmente úteis quando você está inspecionando o estado do aplicativo ou tentando saber mais sobre seu fluxo de execução.  
  
## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Executar para uma função ou local específico  
 Geralmente o método preferencial de depuração de código, esses métodos são úteis quando você sabe exatamente qual código você deseja inspecionar, ou pelo menos você sabe onde deseja iniciar a depuração.  
  
- **Definir pontos de interrupção no código**  
  
     Para definir um ponto de interrupção simples em seu código, abra o arquivo de origem no editor do Visual Studio. Defina o cursor na linha de código onde você deseja suspender a execução e, em seguida, clique com o botão direito do mouse na janela de código para ver o menu de contexto e escolha ponto de interrupção **/inserção** (ou pressione **F9**). O depurador suspende a execução logo antes da linha ser executada.  
  
     ![Definir um ponto de interrupção](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Os pontos de interrupção no Visual Studio fornecem um conjunto rico de funcionalidades adicionais, como pontos de interrupção e pontos de monitoramento condicionais. Consulte [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
- **Executar até o local do cursor**  
  
     Para executar a localização do cursos, coloque o cursor em uma linha executável do código em uma janela de origem. No menu de contexto do editor (clique com o botão direito do mouse no editor), escolha **executar até o cursor**. Isso é como definir um ponto de interrupção temporário.  
  
- **Interromper manualmente o código**  
  
     Para dividir a próxima linha de código disponível em um aplicativo em execução, escolha **depurar**, **interromper tudo** (teclado: **Ctrl + Alt + Break**).  
  
     Se você interromper durante a execução do código sem arquivos de origem ou símbolo (. pdb) correspondentes), o depurador exibirá uma página **arquivos de origem não encontrado** ou **símbolos não encontrados** que podem ajudá-lo a encontrar os arquivos apropriados. Consulte [especificar símbolo (. pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Se não for possível acessar os arquivos de suporte, você ainda poderá depurar as instruções de assembly na janela de desmontagem.  
  
- **Executar a uma função na pilha de chamadas.**  
  
     Na janela **pilha de chamadas** (disponível durante a depuração), selecione a função, clique com o botão direito do mouse e escolha **executar até o cursor**. Para rastrear visualmente a pilha de chamadas, consulte [métodos de mapeamento na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Executar numa função especificada pelo nome**  
  
     Você pode instruir o depurador a executar seu aplicativo até atingir uma função especificada. É possível especificar a função por nome ou escolhê-la da pilha de chamadas.  
  
     Para especificar uma função por nome, escolha **depurar**, **novo ponto de interrupção**, **interromper na função**e, em seguida, insira o nome da função e outras informações de identificação.  
  
     ![Caixa de diálogo novo ponto de interrupção](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Se a função estiver sobrecarregada ou estiver em vários namespaces, você poderá escolher as funções desejadas na caixa de diálogo **escolher pontos de interrupção** .  
  
     ![Caixa de diálogo escolher pontos de interrupção](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Mover o ponteiro para alterar o fluxo de execução  
 Enquanto o depurador está em pausa, você pode mover o ponteiro de instrução para definir a próxima instrução de código a ser executada. Uma seta amarela na margem de uma fonte ou janela de desmontagem marca o local da próxima instrução a ser executada. Movendo essa seta, você pode ignorar uma parte do código ou retornar a uma linha executada anteriormente. É possível usar esse procedimento para situações como ignorar uma seção de código que contém um bug conhecido.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 {1&gt;Para definir a instrução a ser executada&lt;1}, use um destes procedimentos:  
  
- Em uma janela de origem, arraste a seta amarela para um local onde você deseja definir a instrução seguinte no mesmo arquivo de origem  
  
- Em uma janela de origem, defina o cursor na linha que você deseja executar em seguida, clique com o botão direito do mouse e escolha **definir próxima instrução**.  
  
- Na janela de desmontagem, defina o cursor na instrução do assembly que você deseja executar em seguida, clique com o botão direito do mouse em um e escolha **definir próxima instrução**.  
  
> [!CAUTION]
> Definir a instrução a seguir faz com que o contador do programa pule diretamente para a nova localização. Use este comando com cuidado:  
> 
> - As instruções entre os pontos de execução antigos e novos não são executadas.  
>   - Se você mover o ponto de execução para trás, as instruções intervenientes não serão desfeitas.  
>   - Mover a instrução seguinte para outra função ou escopo normalmente resulta em danos à pilha de chamadas, causando um erro em tempo de execução ou uma exceção. Se você tentar mover a instrução seguinte para outro escopo, o depurador abrirá uma caixa de diálogo com um aviso e dará uma chance de cancelar a operação. No Visual Basic, você não pode mover a instrução seguinte para outro escopo ou função.  
>   - No C++ nativo, se você tiver as verificações de tempo de execução ativadas, definir a instrução seguinte poderá fazer com que uma exceção seja gerada quando a execução chegar ao final do método.  
>   - Quando a opção Editar e Continuar está habilitada, **Definir Próxima Instrução** falha caso você tenha feito edições que Editar e Continuar não pode remapear imediatamente. Isso pode ocorrer, por exemplo, se você editou o código dentro de um bloco catch. Quando isso acontecer, você verá uma mensagem de erro informando que não há suporte para a operação.  
> 
> [!NOTE]
> No código gerenciado, você não pode mover a instrução seguinte nas seguintes circunstâncias:  
> 
> - A instrução a seguir é um método diferente do que a instrução atual.  
>   - A depuração foi iniciada com a depuração Just-In-Time.  
>   - Um desenrolamento de pilha de chamada está em andamento.  
>   - Uma exceção System.StackOverflowException ou System.Threading.ThreadAbortException foi lançada.  
  
 Não é possível definir a próxima instrução durante a execução ativa do seu aplicativo. Para definir a próxima instrução, o depurador deve estar no modo de interrupção.  
  
## <a name="step-into-non-user-code"></a>Entrar no código de não-usuário  
 Por padrão, o depurador tenta mostrar apenas o código do aplicativo durante a depuração, que é determinado por uma configuração de depurador chamada *apenas meu código*. (Consulte [apenas meu código](../debugger/just-my-code.md) para ver como isso funciona para diferentes tipos de projeto e idiomas e como você pode personalizar o comportamento.) No entanto, às vezes, enquanto você estiver Depurando, convém examinar o código da estrutura, o código de biblioteca de terceiros ou as chamadas para o sistema operacional (chamadas do sistema).  
  
 Você pode desativar apenas meu código acessando **ferramentas**  /  **Opções**  /  **depuração** e desmarque a caixa de seleção **habilitar apenas meu código** .  
  
 Quando Apenas Meu Código está desabilitado, o depurador pode entrar no código de não-usuário e o código que não é do usuário aparece nas janelas do depurador.  
  
> [!NOTE]
> Apenas Meu Código não é suportada para projetos de dispositivo.  
  
 **Chamadas de entrada no sistema**  
  
 Se você carregou símbolos de depuração para o código do sistema e Apenas Meu Código não estiver habilitado, você poderá entrar em uma chamada do sistema da mesma forma que qualquer outra chamada.  
  
 Para acessar os arquivos de símbolo da Microsoft, consulte [usar servidores de símbolo para localizar arquivos de símbolo que não estejam em seu computador local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) no tópico [especificar símbolo (. pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
 Para carregar símbolos para um componente do sistema específico enquanto você depura:  
  
1. Abra a janela módulos (teclado: **Ctrl + Alt + U**).  
  
2. Selecione o módulo para os quais você deseja carregar os símbolos.  
  
     Você pode saber quais módulos têm símbolos carregados examinando a coluna **status do símbolo** .  
  
3. Escolha **carregar símbolos** no menu de contexto.  
  
## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Intervir em propriedades e operadores no código gerenciado  
 O depurador considera propriedades e operadores no código gerenciado por padrão. Na maioria dos casos, isso proporciona uma melhor experiência de depuração. Para habilitar a depuração em Propriedades ou operadores, escolha opções de **depuração**  /  **Options**. Na página **depuração**  /  **geral** , desmarque a caixa de seleção **passar por propriedades e operadores (somente gerenciados)**
