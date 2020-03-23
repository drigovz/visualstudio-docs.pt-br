---
title: Usando pontos de interrupção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: 63
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadaf069bb53c9d212e6de5ebd6ea2cf9efe7bb1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302465"
---
# <a name="using-breakpoints"></a>Usando pontos de interrupção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Você pode definir pontos de interrupção quando quiser parar a execução do depurador, talvez para ver o estado das variáveis de código ou para olhar a pilha de chamadas. Eles são uma das técnicas de depuração mais importantes na caixa de ferramentas de um desenvolvedor.
  
## <a name="setting-a-function-breakpoint-in-source-code"></a><a name="BKMK_Overview"></a>Definindo um ponto de ruptura de função no código-fonte  
 Você define um ponto de ruptura de função no código-fonte clicando na margem esquerda de um arquivo de código fonte, ou colocando seu cursor em uma linha de código e pressionando F9. O ponto de ruptura aparece como um ponto vermelho na margem esquerda, e a linha de código também é colorida:  
  
 ![Defina um ponto de ruptura](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Quando você executa este código no depurador, a execução pára sempre que o ponto de ruptura é atingido, antes que o código dessa linha seja executado. A linha de código-fonte é amarela colorida:  
  
 ![Execução de breakpoint interrompida](../debugger/media/breakpointexecution.png "Execução de pontos de ruptura")  
  
 Neste ponto o `testInt` valor de ainda é 1.  
  
 Você pode olhar para o estado atual do aplicativo, incluindo valores variáveis e a pilha de chamadas. Para obter mais informações sobre a pilha de chamadas, consulte [Como: Usar a janela de pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 Você pode definir um ponto de ruptura em qualquer linha de código executável. Por exemplo, no código C# acima, você pode definir `for` um ponto de ruptura `for` na declaração variável, no loop ou em qualquer código dentro do loop, mas você não pode definir um ponto de ruptura no namespace ou declarações de classe ou na assinatura do método.  
  
## <a name="setting-other-kinds-of-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Definindo outros tipos de pontos de interrupção  
 Você também pode definir pontos de interrupção na pilha de chamadas, na janela Desmontagem e, no código C++ nativo, em uma condição de dados ou em um endereço de memória.  
  
## <a name="setting-a-breakpoint-in-the-call-stack-window"></a><a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Configuração de um ponto de ruptura na janela de pilha de chamadas  
 Você pode interromper a execução na instrução ou linha para a que uma função de chamada retorna definindo um ponto de ruptura na janela **Pilha de chamadas.** Para obter mais informações sobre a pilha de chamadas, consulte [Como: Usar a janela de pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md). O depurador deve ter parado de ser executado.  
  
1. Comece a depurar o aplicativo e a execução de espera seja interrompida (por exemplo, em um ponto de ruptura). Abra a janela **Call Stack** **(Debug / Windows / Call Stack**, ou **CTRL + ALT + C**).  
  
2. Clique com o botão direito do mouse na função de chamada e, em seguida, selecione **Breakpoint / Insert Breakpoint**, ou apenas use a tecla de atalho **F9**.  
  
3. Um símbolo de ponto de ruptura aparece na margem esquerda da pilha de chamadas, ao lado do nome de chamada da função.  
  
   Na janela **Pontos de interrupção,** o ponto de interrupção da pilha de chamadas aparece como um endereço com um local de memória que corresponde à próxima instrução executável na função. O depurador interrompe a execução na instrução.  
  
   Para rastrear visualmente pontos de interrupção durante a execução do código, consulte [Métodos de mapa na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Configuração de um ponto de ruptura na janela de desmontagem  
 Para definir um ponto de interrupção em uma instrução de assembly, o depurador deve estar no modo de interrupção.  
  
1. Comece a depurar o aplicativo e a execução de espera seja interrompida (por exemplo, em um ponto de ruptura). Abra a janela **de desmontagem** **(Debug / Windows / Desassembly**, ou **Ctrl + Alt + D**).  
  
2. Clique na margem esquerda na instrução em que deseja quebrar ou defina o cursor na instrução e **pressione F9**.  
  
## <a name="setting-a-data-breakpoint-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Definindo um ponto de ruptura de dados (somente C++ nativo)  
 Os pontos de interrupção de dados quebram a execução quando um valor armazenado em um endereço de memória especificado é alterado. Se o valor for lido, mas não alterado, a execução não quebrará. Para definir pontos de interrupção de dados, o depurador deve estar em modo de interrupção.  
  
1. Comece a depurar o aplicativo e aguarde até que um ponto de ruptura seja alcançado. No menu **Debug,** escolha **Novo Breakpoint / Data Breakpoint** (ou abra a janela **Breakpoints** e escolha **Novo / Data Breakpoint**.  
  
2. Na **caixa Endereço,** digite um endereço de memória ou uma expressão que seja avaliada em um endereço de memória. Por exemplo, `&avar` digite para quebrar `avar` quando o conteúdo da variável mudar.  
  
3. No **downdown byte count,** selecione o número de bytes que deseja que o depurador assista. Por exemplo, se você selecionar **4**, o depurador `&avar` observará os quatro bytes a partir de e quebrará se algum desses bytes mudar de valor.  
  
   Tenha em mente que os pontos de interrupção de dados dependem da aplicabilidade de endereços de memória específicos.  
  
- O endereço de uma variável muda de uma sessão de depuração para a próxima. Os pontos de interrupção de dados são automaticamente desativados no final de cada sessão de depuração.  
  
- Se você definir um ponto de ruptura de dados em uma variável local, o ponto de ruptura permanece ativado quando a função termina, mas o endereço de memória não é mais aplicável e o comportamento do ponto de ruptura é imprevisível. Se você definir um ponto de ruptura de dados em uma variável local, você deve remover ou desativar o ponto de ruptura antes que a função termine.  
  
  Pontos de interrupção não funcionam nestas condições:  
  
- Um processo que não está sendo depurado grava para o local de memória  
  
- O local de memória é compartilhado entre dois ou mais processos  
  
- O local de memória é atualizado dentro do kernel. Por exemplo, se a memória for passada `ReadFile` para a função Windows de 32 bits, a memória será atualizada a partir do modo kernel e o depurador não quebrará na gravação de memória.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Configuração de um breakpoint com um endereço de memória (somente C++ nativo)  
 Você também pode usar o endereço de um objeto para definir um ponto de ruptura em um método chamado em uma instância específica de uma classe.  Aqui está um exemplo:  
  
 Por exemplo, dado `my_class` um objeto de tipo com o endereço, `my_method` você pode definir um ponto de ruptura de função em um método chamado a partir dessa instância.  
  
1. Defina um ponto de ruptura em algum lugar após essa instância da classe é instanciado.  
  
2. Encontre o endereço da instância (vamos dizer `0xcccccccc`que é ).  
  
3. Clique **em Debug / Novo Breakpoint / Function Breakpoint** (ou **ALT + F9, B**).  
  
4. Adicione o seguinte texto à caixa **Nome da função:**  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
## <a name="managing-breakpoints"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Gerenciamento de pontos de interrupção  
 Você pode usar a janela **Breakpoints** **(Debug / Windows / Breakpoints**, ou **CTRL + ALT + B**) para ver todos os pontos de interrupção que você definiu em sua solução:  
  
 ![Janela de pontos de interrupção](../debugger/media/breakpointswindow.png "Janela de pontos de interrupção")  
  
 A janela **Breakpoints** oferece um lugar central para gerenciar todos os seus pontos de interrupção, o que pode ser especialmente útil em uma solução grande ou em um cenário complexo de depuração onde os pontos de interrupção são críticos. Se você precisar salvar ou compartilhar o estado e a localização de um conjunto de pontos de interrupção, você pode exportar e importar pontos de interrupção somente a partir da janela **Breakpoints.**  
  
## <a name="advanced-breakpoints"></a><a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Pontos de interrupção avançados  
  
## <a name="breakpoint-conditions"></a>Condições de ponto de interrupção  
 Você pode controlar quando e onde um ponto de ruptura é executado definindo condições.  
  
1. Clique com o botão direito do mouse no ponto de partida ou paire sobre o ponto de partida e escolha o ícone de configurações.  
  
2. No menu contexto, selecione **Condições**. Isso abre a janela **Configurações de ponto de ruptura:**  
  
   ![Configurações de ponto de ruptura](../debugger/media/breakpointsettings.png "Configurações de ponto de ruptura")  
  
   Quando você verifica a caixa **Condições,** a janela se expande para mostrar os diferentes tipos de condições.  
  
   **Expressão condicional:** Quando você seleciona Expressão Condicional, você pode escolher duas condições: **É verdadeira** e **Quando alterada**. Escolher **É verdade** se você quiser quebrar quando a expressão está satisfeita, ou escolher Quando **alterado** se você quiser quebrar quando o valor da expressão foi alterado.  
  
   No exemplo a seguir, definimos o ponto `testInt` de ruptura para bater somente quando o valor for **4**:  
  
   ![A condição de ponto de ruptura é verdadeira](../debugger/media/breakpointconditionistrue.png "Condição de ponto de rupturaÉtrue")  
  
   No exemplo a seguir, definimos o ponto `testInt` de breakpoint para atingir somente quando o valor das alterações:  
  
   ![Ponto de ruptura quando alterado](../debugger/media/breakpointwhenchanged.png "Ponto de rupturaQuandoalterado")  
  
   O comportamento do campo Quando alterado é diferente para diferentes linguagens de programação. Se você escolher **Quando alterado** para código nativo, o depurador não considera a primeira avaliação da condição como uma alteração, de modo que o ponto de ruptura não será atingido na primeira avaliação. Se você escolher **Quando alterado** para código gerenciado, ele será atingido na primeira avaliação depois de **Quando alterado** é selecionado.  
  
   Se você definir uma condição de ponto de ruptura com sintaxe inválida, uma mensagem de aviso será exibida. Se você especificar uma condição de ponto de interrupção com sintaxe válida mas semântica inválida, uma mensagem de aviso aparecerá na primeira vez em que o ponto de interrupção for atingido. Em qualquer um dos casos, o depurador interromperá a execução quando o ponto de interrupção inválido for atingido. O ponto de partida só é ignorado se `false`a condição for válida e avaliar para .  
  
   A condição pode ser qualquer expressão válida que seja reconhecida pelo depurador. Para obter mais informações sobre expressões válidas, consulte [Expressões no Depurador](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Usando IDs de objeto em condições de ponto de ruptura (C# e F#)  
 Há momentos em que você deseja observar o comportamento de um objeto específico; por exemplo, você pode querer descobrir por que um objeto foi inserido mais de uma vez em uma coleção. Em C# e F#, você pode criar IDs de objeto para instâncias específicas de tipos de [referência](https://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) e usá-los em condições de ponto de ruptura. O ID do objeto é gerado pelos serviços de depuração de tempo de execução de idioma comum (CLR) e associado ao objeto.  Para criar uma ID de objeto, faça o seguinte:  
  
1. Defina um ponto de ruptura no código algum tempo após a criação do objeto.  
  
2. Inicie a depuração e, quando a execução parar no ponto de ruptura, encontre o ponto de ruptura na janela **Locals,** clique com o botão direito do mouse e selecione **Fazer ID de objeto**.  
  
    Você deve **$** ver um número mais um na janela **local.** Este é o id do objeto.  
  
3. Adicione um novo ponto de ruptura condicional no ponto que você deseja investigar, por exemplo, quando o objeto deve ser adicionado à coleção.  
  
4. Use o ID do objeto no campo Expressão Condicional. Por exemplo, se houver `item` uma variável referente ao objeto a ser adicionado à coleção, você colocaria o **item == $n**, onde **n** é o número de ID do objeto.  
  
    A execução será rompida no momento em que esse objeto deve ser adicionado à coleção.  
  
   Mais tarde, se você quiser excluir o ID do objeto, você pode clicar com o botão direito do mouse na variável na janela **Locals** e selecionar **Excluir ID de objeto**.  
  
   Observe que os IDs do objeto criam referências fracas e não impedem que o objeto seja coletado. Eles são válidos apenas para a sessão de depuração atual.  
  
## <a name="hit-count"></a>Contagem de Ocorrências  
 Se você suspeitar que um loop em seu código começa a se comportar mal após um certo número de iterações, você pode definir um ponto de ruptura para interromper a execução após um número especificado de acessos à linha de código associada, em vez de ser forçado a pressionar repetidamente **F5** para atingir o nível de iteração.  
  
 Na janela **Configurações de ponto de** intervalo, defina a condição de **Contagem de Impacto**. Em seguida, você pode especificar o número de iterações. No exemplo a seguir, definimos o ponto de ruptura para acertar em todas as outras iterações:  
  
 ![Contagem de acertos de breakpoint](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtrar  
 Você pode restringir um ponto de ruptura para disparar apenas em dispositivos especificados ou em processos e segmentos especificados.  
  
 Na janela configuração de ponto de **ruptura,** defina a condição como **Filtrar**. Digite uma ou mais das seguintes expressões.  
  
- MachineName = "nome"  
  
- ProcessId = valor  
  
- ProcessName = "nome"  
  
- ThreadId = valor  
  
- ThreadName = "nome"  
  
  Ensine os valores da seqüência em aspas duplas. Você pode combinar `&` cláusulas `||` usando (And), (OR), `!` (NOT) e parênteses.  
  
## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Ações e pontos de rastreamento de breakpoint  
 Um tracepoint é um ponto de interrupção que imprime uma mensagem na janela de Saída. Um tracepoint pode funcionar como uma declaração de rastreamento temporária na linguagem de programação.  
  
 Na janela **Configurações de ponto de** intervalo, verifique a caixa **Ações.** Escolha **Registrar uma mensagem para a janela Saída** no grupo **Ação.** Você pode imprimir uma seqüência genérica, como **este é um teste**. Para incluir o valor de uma variável ou expressão, inclua-o em aparelhos encaracolados.  
  
 Para interromper a execução quando o ponto de rastreamento for atingido, limpe a caixa de **seleção continuar execução.** Quando **a execução contínua** é verificada, a execução não é interrompida. Nos dois casos, a mensagem é impressa.  
  
 Você pode usar as seguintes palavras-chave especiais na **Mensagem**.  
  
|||  
|-|-|  
|**$ADDRESS**|Instrução atual|  
|**$CALLER**|Nome da função de chamada|  
|**$CALLSTACK**|Pilha de chamadas|  
|**$FUNCTION**|Nome da função atual|  
|**$PID**|Id de processo|  
|**$PNAME**|Nome do processo|  
|**$TID**|id do thread|  
|**$TNAME**|Nome do thread|  
|**$TICK**||  
|**$TNAME**||  
  
## <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Rótulos breakpoint  
 Os rótulos breakpoint são usados apenas na janela **Breakpoints** para classificar e filtrar a lista de pontos de interrupção. Para adicionar um rótulo a um ponto de breakpoint, escolha a linha de ponto de ruptura e escolha **'Rótulo'** no menu de contexto.  
  
## <a name="export-and-import-breakpoints"></a>Pontos de interrupção de exportação e importação  
 Você pode exportar um ponto de ruptura para um arquivo XML clicando com o botão direito do mouse no ponto de ruptura e selecionando **Exportar**. O arquivo é salvo por padrão no diretório de soluções. Para importar pontos de interrupção, abra a janela **Pontos de interrupção** **(CTRL + ALT + B**) e na barra de ferramentas clique na seta de apontar para o botão direito (a dica de ferramenta é Importar pontos de interrupção de um **arquivo**).  
  
## <a name="troubleshoot-breakpoints"></a>Solucionar problemas de pontos de interrupção  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Eu deletei um ponto de ruptura, mas eu continuo a atingi-lo quando eu começar a depurar novamente  
 Se você excluiu um ponto de breakpoint durante a depuração, em alguns casos você pode atingir o ponto de ruptura novamente na próxima vez que você começar a depurar. Para parar de atingir esse ponto de interrupção, certifique-se de que todas as instâncias do breakpoint sejam removidas da janela **Breakpoints.**  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>O depurador não pode localizar a versão correta do arquivo de origem de um ponto de interrupção  
 Se um arquivo de origem tiver sido alterado e se a fonte não corresponder mais ao código que você estiver depurando, o depurador poderá localizar o arquivo de origem que corresponda a um ponto de interrupção, mesmo se o arquivo de origem existir.  
  
1. Se você quiser que o Visual Studio exiba código-fonte que não corresponda à versão que você está depurando, escolha **Debug / Opções e Configurações**. Na página **Depuração/Geral,** limpe os **arquivos de origem Derequire que correspondam exatamente à** opção de versão original.  
  
2. Você também pode associar o ponto de interrupção ao arquivo de origem. Selecione o ponto de ruptura e escolha **Condições** no menu de contexto. Verificar **Permitir que o código-fonte seja diferente do original** na janela **Configurações de ponto de** ruptura.  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Os pontos de interrupção não funcionam em uma DLL  
 Você não pode definir um ponto de interrupção em um arquivo de origem quando o depurador não carregou informações de depuração do módulo no qual o código está localizado. Os sintomas podem incluir mensagens como **o ponto de ruptura não será definido**. O glifo de ponto de interrupção Aviso aparece no local do ponto de interrupção. No entanto, esses pontos de interrupção de Aviso tornam-se pontos de interrupção reais quando o código é carregado. Para obter mais informações sobre símbolos de carregamento, consulte [Especificar símbolo (.pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Navegando através do Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)
