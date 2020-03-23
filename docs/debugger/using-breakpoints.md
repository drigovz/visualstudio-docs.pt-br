---
title: Use pontos de interrupção no depurador | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
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
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302031"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Use pontos de interrupção no depurador do Visual Studio

Os breakpoints são uma das técnicas de depuração mais importantes na caixa de ferramentas do seu desenvolvedor. Você define pontos de interrupção onde quiser pausar a execução do depurador. Por exemplo, você pode querer ver o estado das variáveis de código ou olhar para a pilha de chamadas em um determinado ponto de ruptura.  Se você estiver tentando resolver um aviso ou problema ao usar pontos de interrupção, consulte [Pontos de interrupção de solução de problemas no depurador do Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Se você conhece a tarefa ou o problema que está tentando resolver, mas precisa saber que tipo de ponto de ruptura usar, consulte [Encontrar sua tarefa de depuração](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Definir pontos de interrupção no código-fonte

Você pode definir um ponto de ruptura em qualquer linha de código executável. Por exemplo, no seguinte código C#, você pode definir um `for` ponto de ruptura `for` na declaração variável, no loop ou em qualquer código dentro do loop. Você não pode definir um ponto de ruptura no namespace ou declarações de classe, ou na assinatura do método.

Para definir um ponto de ruptura no código-fonte, clique na margem esquerda ao lado de uma linha de código. Você também pode selecionar a linha e pressionar **F9**, selecione **Debug** > **Toggle Breakpoint**ou clique com o botão direito do mouse e selecione **Breakpoint** > **Insert breakpoint breakpoint**. O ponto de ruptura aparece como um ponto vermelho na margem esquerda.

Para a maioria dos idiomas, incluindo C#, as linhas de execução de ponto de ruptura e de execução atual são automaticamente destacadas. Para o código C++, você pode ativar o destaque das linhas de breakpoint e atuais selecionando **Ferramentas** (ou **Debug**) >**Depuração** >  de **Opções** > **Destaque toda a linha de origem para pontos de interrupção e somente declaração atual (somente C++).**

![Defina um ponto de ruptura](../debugger/media/basicbreakpoint.png "Ponto de ruptura básico")

Quando você depura, a execução faz uma pausa no ponto de ruptura, antes que o código dessa linha seja executado. O símbolo do ponto de ruptura mostra uma seta amarela.

No ponto de ruptura no exemplo `testInt` a seguir, o valor de ainda é 1. Assim, o valor não mudou desde que a variável foi inicializada (definida como um valor de 1) porque a declaração em amarelo ainda não foi executada.

![Execução de breakpoint interrompida](../debugger/media/breakpointexecution.png "Execução de breakpoint")

Quando o depurador pára no ponto de ruptura, você pode olhar para o estado atual do aplicativo, incluindo [valores variáveis](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) e a [pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).

Aqui estão algumas instruções gerais para trabalhar com pontos de interrupção.

- O ponto de ruptura é um alternador. Você pode clicar nele, pressionar **F9**ou usar **Debug** > **Toggle Breakpoint** para excluí-lo ou reinseri-lo.

- Para desativar um ponto de ruptura sem excluí-lo, clique no mouse ou com o botão direito do mouse e **selecione Desativar ponto de ruptura**. Os pontos de interrupção desativados aparecem como pontos vazios na margem esquerda ou na janela **Pontos de interrupção.** Para reativar um ponto de breakpoint, passar o mouse ou o botão direito do mouse e selecionar **Ativar ponto de ruptura**.

- Defina condições e ações, adicione e edite rótulos ou exporte um ponto de ruptura clicando com o botão direito do mouse e selecionando o comando apropriado ou pairando sobre ele e selecionando o ícone **Configurações.**

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Ações de ponto de interrupção e pontos de rastreamento

Um *tracepoint* é um ponto de interrupção que imprime uma mensagem na janela de **Saída**. Um tracepoint pode agir como uma declaração de rastreamento temporário na linguagem de programação e não pausa a execução do código. Você cria um tracepoint definindo uma ação especial na janela **Configurações de ponto de** ruptura. Para obter instruções detalhadas, consulte [Usar pontos de rastreamento no depurador visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Condições de ponto de interrupção

Você pode controlar quando e onde um ponto de ruptura é executado definindo condições. A condição pode ser qualquer expressão válida que o depurador reconhece. Para obter mais informações sobre expressões válidas, confira [Expressões no depurador](../debugger/expressions-in-the-debugger.md).

**Para definir uma condição de ponto de ruptura:**

1. Clique com o botão direito do mouse no símbolo breakpoint e selecione **Condições**. Ou passar o tempo sobre o símbolo de ponto de ruptura, selecione o ícone **Configurações** e selecione **Condições** na janela **Configurações de ponto** de ruptura.

   Você também pode definir condições na janela **Pontos de interrupção** clicando com o botão direito do mouse em um ponto de interrupção e selecionando **Configurações**e, em seguida, selecionando **Condições**.

   ![Configurações de ponto de ruptura](../debugger/media/breakpointsettings.png "Configurações de ponto de ruptura")

2. Na lista de queda, selecione **Expressão Condicional,** **Aperte contagem**ou **filtro**e defina o valor de acordo.

3. Selecione **Fechar** ou pressionar **Ctrl**+**Enter** para fechar a janela **Configurações de ponto de ruptura.** Ou, a partir da janela **Pontos de interrupção,** selecione **OK** para fechar a caixa de diálogo.

Pontos de interrupção com condições definidas aparecem com um **+** símbolo nas janelas código-fonte e Pontos de **Interrupção.**

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Crie uma expressão condicional

Quando você seleciona **Expressão Condicional,** você pode escolher entre duas condições: **É verdadeiro** ou **Quando alterado**. Escolha **É verdade** para quebrar quando a expressão está satisfeita, ou quando **alterada** para quebrar quando o valor da expressão foi alterado.

No exemplo a seguir, o ponto de `testInt` partida é atingido somente quando o valor de **é 4**:

![A condição de ponto de ruptura é verdadeira](../debugger/media/breakpointconditionistrue.png "Breakpoint é verdade")

No exemplo a seguir, o ponto de `testInt` partida é atingido somente quando o valor das alterações:

![Ponto de ruptura Quando alterado](../debugger/media/breakpointwhenchanged.png "Ponto de ruptura Quando alterado")

Se você definir uma condição de ponto de ruptura com sintaxe inválida, uma mensagem de aviso será exibida. Se você especificar uma condição de ponto de interrupção com sintaxe válida mas semântica inválida, uma mensagem de aviso aparecerá na primeira vez em que o ponto de interrupção for atingido. Em ambos os casos, o depurador quebra quando atinge o ponto de ruptura inválido. O ponto de partida só é ignorado se `false`a condição for válida e avaliar para .

>[!NOTE]
>O comportamento do campo **Quando alterado** é diferente para diferentes linguagens de programação.
>- Para código nativo, o depurador não considera a primeira avaliação da condição como uma mudança, portanto não atinge o ponto de ruptura na primeira avaliação.
>- Para código gerenciado, o depurador atinge o ponto de ruptura na primeira avaliação após **quando alterado** é selecionado.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Use ids de objeto em expressões condicionais (somente C# e F#)

 Há momentos em que você quer observar o comportamento de um objeto específico. Por exemplo, você pode querer descobrir por que um objeto foi inserido em uma coleção mais de uma vez. Em C# e F#, você pode criar IDs de objeto para instâncias específicas de tipos de [referência](/dotnet/csharp/language-reference/keywords/reference-types)e usá-los em condições de ponto de ruptura. O ID do objeto é gerado pelos serviços de depuração de tempo de execução de idioma comum (CLR) e associado ao objeto.

**Para criar um ID de objeto:**

1. Defina um ponto de ruptura no código em algum lugar após a criação do objeto.

2. Iniciar a depuração e, quando a execução for pausada no ponto de ruptura, selecione **Depurar** > **Pontos do** **Windows** > ou **Alt**+**4** para abrir a janela **Locais.**

   Encontre a instância específica do objeto na janela **Locals,** clique com o botão direito do mouse e selecione **Fazer ID de objeto**.

   Você deve **$** ver um número mais um na janela **local.** Este é o id do objeto.

3. Adicione um novo ponto de ruptura no ponto que você deseja investigar; por exemplo, quando o objeto deve ser adicionado à coleção. Clique com o botão direito do mouse no ponto de interrupção e selecione **Condições**.

4. Use o ID do objeto no campo **Expressão Condicional.** Por exemplo, se `item` a variável for o objeto a ser adicionado à coleção, selecione **É verdadeiro** e digite **item == $\<n>**, onde \<n> é o número de ID do objeto.

   A execução será rompida no momento em que esse objeto deve ser adicionado à coleção.

   Para excluir o ID do objeto, clique com o botão direito do mouse na variável na janela **Locals** e selecione **Excluir ID de objeto**.

> [!NOTE]
> Os IDs do objeto criam referências fracas e não impedem que o objeto seja coletado. Eles são válidos apenas para a sessão de depuração atual.

### <a name="set-a-hit-count-condition"></a>Defina uma condição de contagem de hits

Se você suspeitar que um loop em seu código começa a se comportar mal após um certo número de iterações, você pode definir um ponto de ruptura para parar a execução após esse número de acessos, em vez de ter que pressionar repetidamente **F5** para alcançar essa iteração.

Em **Condições** na janela **Configurações de ponto de ruptura,** selecione **Contagem de**impactos e especifique o número de iterações. No exemplo a seguir, o ponto de partida é definido para acertar em todas as outras iterações:

![Contagem de acertos de breakpoint](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Defina uma condição de filtro

Você pode restringir um ponto de ruptura para disparar apenas em dispositivos especificados ou em processos e segmentos especificados.

Em **Condições** na janela **Configurações de ponto de intervalo,** selecione **Filtro**e digite uma ou mais das seguintes expressões:

- MachineName = "nome"
- ProcessId = valor
- ProcessName = "nome"
- ThreadId = valor
- ThreadName = "nome"

Ensine os valores da seqüência em aspas duplas. Você pode combinar `&` cláusulas `||` usando (And), (OR), `!` (NOT) e parênteses.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Definir pontos de interrupção da função

Você pode interromper a execução quando uma função é chamada. Isso é útil, por exemplo, quando você sabe o nome da função, mas não sua localização. Também é útil se você tiver funções com o mesmo nome e quiser quebrar todas elas (como funções sobrecarregadas ou funções em diferentes projetos).

**Para definir um ponto de ruptura de função:**

1. Selecione **Debug** > **New Breakpoint** > **Function Breakpoint**ou **pressione Alt**+**F9** > **Ctrl**+**B**.

   Você também pode selecionar **Novo** > **Ponto de Interrupção de Função** na janela Pontos de **interrupção.**

1. Na caixa de diálogo **'Ponto de ruptura da nova função',** digite o nome da função na caixa **Nome da função.**

   Para reduzir a especificação da função:

   - Use o nome da função totalmente qualificado.

     Exemplo: `Namespace1.ClassX.MethodA()`

   - Adicione os tipos de parâmetro de uma função sobrecarregada.

     Exemplo: `MethodA(int, string)`

   - Use o símbolo '!' para especificar o módulo.

     Exemplo: `App1.dll!MethodA`

   - Use o operador de contexto em C++nativo.

     `{function, , [module]} [+<line offset from start of method>]`

     Exemplo: `{MethodA, , App1.dll}+2`

1. No **dropdown** do idioma, escolha a linguagem da função.

1. Selecione **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Defina um ponto de ruptura de função usando um endereço de memória (somente C++ nativo)
 Você pode usar o endereço de um objeto para definir um ponto de ruptura de função em um método chamado por uma instância específica de uma classe.  Por exemplo, dado um `my_class`objeto endereçado de tipo, você pode definir um ponto de ruptura de função no método que a `my_method` instância chama.

1. Defina um ponto de ruptura em algum lugar após a instância da classe ser instanciada.

2. Encontre o endereço da instância `0xcccccccc`(por exemplo, ).

3. Selecione **Debug** > **New Breakpoint** > **Function Breakpoint**ou **pressione Alt**+**F9** > **Ctrl**+**B**.

4. Adicione o seguinte à caixa **Nome da função** e selecione o idioma **C++.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Defina pontos de interrupção de dados (.NET Core 3.0 ou superior)

Os pontos de interrupção de dados quebram a execução quando a propriedade de um objeto específico é alterada.

**Para definir um ponto de ruptura de dados**

1. Em um projeto .NET Core, inicie a depuração e espere até que um ponto de ruptura seja atingido.

2. Na janela **Autos**, **Watch**ou **Locals,** clique com o botão direito do mouse em uma propriedade e selecione Quebrar quando o **valor mudar** no menu de contexto.

    ![Ponto de ruptura de dados gerenciado](../debugger/media/managed-data-breakpoint.png "Ponto de ruptura de dados gerenciado")

Pontos de interrupção de dados no .NET Core não funcionarão para:

- Propriedades que não podem ser expandidas na dica de ferramentas, locais, autos ou janela do relógio
- Variáveis estáticas
- Classes com o atributo DebuggerTypeProxy
- Campos dentro de estruturas

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Defina pontos de interrupção de dados (somente C++ nativo)

 Os pontos de interrupção de dados quebram a execução quando um valor armazenado em um endereço de memória especificado é alterado. Se o valor for lido, mas não alterado, a execução não quebrará.

**Para definir um ponto de ruptura de dados:**

1. Em um projeto C++, comece a depurar e espere até que um ponto de ruptura seja alcançado. No menu **Debug,** escolha **Novo ponto** > de**ruptura de dados**

    Você também pode selecionar **Novo** > **ponto de interrupção de dados** na janela Pontos de **interrupção** ou clicar com o botão direito do mouse em um item na janela **Autos,** **Watch**ou **Locals** e selecionar Quebrar quando o **valor muda** no menu de contexto.

2. Na **caixa Endereço,** digite um endereço de memória ou uma expressão que seja avaliada em um endereço de memória. Por exemplo, `&avar` digite para quebrar `avar` quando o conteúdo da variável mudar.

3. No **downdown byte count,** selecione o número de bytes que deseja que o depurador assista. Por exemplo, se você selecionar **4**, o depurador `&avar` observará os quatro bytes a partir de e quebrará se algum desses bytes mudar de valor.

Os pontos de interrupção de dados não funcionam nas seguintes condições:
- Um processo que não estiver sendo depurado grava na localização da memória.
- A localização de memória é compartilhada entre dois ou mais processos.
- O local de memória é atualizado dentro do kernel. Por exemplo, se a memória for passada `ReadFile` para a função Windows de 32 bits, a memória será atualizada a partir do modo kernel, para que o depurador não quebre na atualização.
- Onde a expressão do relógio é maior que 4 bytes em hardware de 32 bits e 8 bytes em hardware de 64 bits. Esta é uma limitação da arquitetura x86.

> [!NOTE]
> - Os pontos de interrupção de dados dependem de endereços de memória específicos. O endereço de uma variável muda de uma sessão de depuração para a próxima, de modo que os pontos de interrupção de dados são automaticamente desativados no final de cada sessão de depuração.
>
> - Se você definir um ponto de ruptura de dados em uma variável local, o ponto de ruptura permanece ativado quando a função termina, mas o endereço de memória não é mais aplicável, então o comportamento do ponto de ruptura é imprevisível. Se você definir um ponto de ruptura de dados em uma variável local, você deve excluir ou desativar o ponto de ruptura antes que a função termine.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gerenciar pontos de interrupção na janela de Pontos de Interrupção

 Você pode usar a janela **Breakpoints** para ver e gerenciar todos os pontos de interrupção em sua solução. Esse local centralizado é especialmente útil em uma solução grande ou em cenários complexos de depuração onde os pontos de interrupção são críticos.

Na janela **Breakpoints,** você pode pesquisar, classificar, filtrar, ativar/desativar ou excluir pontos de interrupção. Você também pode definir condições e ações, ou adicionar uma nova função ou ponto de ruptura de dados.

Para abrir a janela **Pontos de interrupção,** selecione **Debug** > **Windows** > **Breakpoints**ou pressione **Alt**+**F9** ou **Ctrl**+**Alt**+**B**.

![Janela de pontos de interrupção](../debugger/media/breakpointswindow.png "Janela Pontos de Interrupção")

Para selecionar as colunas a serem exibidas na janela **Pontos de interrupção,** **selecione Mostrar colunas**. Selecione um cabeçalho de coluna para classificar a lista de pontos de interrupção por essa coluna.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Rótulos breakpoint
Você pode usar etiquetas para classificar e filtrar a lista de pontos de interrupção na janela **Breakpoints.**

1. Para adicionar um rótulo a um ponto de interrupção, clique com o botão direito do mouse no ponto de interrupção no código-fonte ou na janela **Pontos de interrupção** e, em seguida, selecione Editar **rótulos**. Adicione um novo rótulo ou escolha um existente e, em seguida, selecione **OK**.
2. Classifique a lista de pontos de interrupção na janela **Pontos de interrupção** selecionando os **cabeçalhos de rótulos,** **condições**ou outras colunas. Você pode selecionar as colunas a serem exibidas selecionando **Mostrar colunas** na barra de ferramentas.

### <a name="export-and-import-breakpoints"></a>Importar e exportar pontos de interrupção
 Para salvar ou compartilhar o estado e a localização de seus pontos de interrupção, você pode exportá-los ou importá-los.

- Para exportar um único ponto de interrupção para um arquivo XML, clique com o botão direito do mouse no ponto de interrupção na janela código-fonte ou **Pontos de interrupção** e selecione **Exportar** ou **Exportar selecionado**. Selecione um local de exportação e selecione **Salvar**. O local padrão é a pasta de solução.
- Para exportar vários pontos de interrupção, na janela **Breakpoints,** selecione as caixas ao lado dos pontos de interrupção ou digite critérios de pesquisa no campo **Pesquisar.** Selecione **Exportar todos os pontos de interrupção correspondentes ao** ícone de critérios de pesquisa atuais e salve o arquivo.
- Para exportar todos os pontos de interrupção, desmarque todas as caixas e deixe o campo **pesquisar** em branco. Selecione **Exportar todos os pontos de interrupção correspondentes ao** ícone de critérios de pesquisa atuais e salve o arquivo.
- Para importar pontos de interrupção, na janela **Pontos de interrupção,** selecione os pontos de interrupção de importar de um ícone **de arquivo,** navegue até o local de arquivo XML e selecione **Abrir**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Defina pontos de interrupção das janelas de depurador

Você também pode definir pontos de interrupção nas janelas de depurador de pilha de **chamadas** e **desmontagem.**

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Defina um ponto de ruptura na janela Call Stack

 Para quebrar a instrução ou a linha para a que uma função de chamada retorna, você pode definir um ponto de ruptura na janela **Pilha de chamadas.**

**Para definir um ponto de intervalo na janela Pilha de chamadas:**

1. Para abrir a janela **'Pilha de chamadas',** você deve ser pausado durante a depuração. Selecione **Depurar** > **pilha de chamadas do****Windows** > ou **pressione Ctrl**+**Alt**+**C**.

2. Na janela **Pilha de chamadas,** clique com o botão direito do mouse na função de chamada e selecione **Breakpoint** > **Insert Breakpoint**ou **pressione F9**.

   Um símbolo de ponto de ruptura aparece ao lado do nome de chamada de função na margem esquerda da pilha de chamadas.

O ponto de interrupção da pilha de chamadas aparece na janela **Pontos de interrupção** como um endereço, com um local de memória que corresponde à próxima instrução executável na função.

O depurador quebra na instrução.

Para obter mais informações sobre a pilha de chamadas, consulte [como: Use a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md).

Para rastrear visualmente pontos de interrupção durante a execução do código, consulte [Métodos de mapa na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Defina um ponto de ruptura na janela de desmontagem

1. Para abrir a janela **Desmontagem,** você deve ser pausado durante a depuração. Selecione **Depurar desmontagem** > **do****Windows** > ou **pressione Alt**+**8**.

2. Na janela **Desmontagem,** clique na margem esquerda da instrução que deseja quebrar. Você também pode selecioná-lo e pressionar **F9**, ou clicar com o botão direito do mouse e selecionar **Breakpoint** > **Insert Breakpoint**.

## <a name="see-also"></a>Confira também

- [O que é depuração?](../debugger/what-is-debugging.md)
- [Escreva melhor código C# usando o Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Primeira olhada na depuração](../debugger/debugger-feature-tour.md)
- [Pontos de interrupção de solução de problemas no depurador do Visual Studio](../debugger/troubleshooting-breakpoints.md)
