---
title: Navegar código com o depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302115"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Navegue pelo código com o depurador do Visual Studio

O depurador do Visual Studio pode ajudá-lo a navegar através do código para inspecionar o estado de um aplicativo e mostrar seu fluxo de execução. Você pode usar atalhos de teclado, comandos de depuração, pontos de interrupção e outros recursos para chegar rapidamente ao código que deseja examinar. A familiaridade com comandos e atalhos de navegação dedepurador torna mais rápido e fácil encontrar e resolver problemas de aplicativos.  Se esta é a primeira vez que você tenta depurar código, você pode querer ler [Depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md) e [técnicas e ferramentas de depuração](../debugger/write-better-code-with-visual-studio.md) antes de passar por este artigo.

## <a name="get-into-break-mode"></a>Entre no "modo de pausa"

No *modo de quebra,* a execução do aplicativo é suspensa enquanto funções, variáveis e objetos permanecem na memória. Uma vez que o depurador esteja no modo de quebra, você pode navegar através do seu código. As maneiras mais comuns de entrar no modo de quebra rapidamente é:

- Inicie a revisão do código pressionando **F10** ou **F11**. Isso permite que você encontre rapidamente o ponto de entrada do seu aplicativo, então você pode continuar pressionando comandos de passo para navegar código.

- [Execute para um local ou função específico,](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)por exemplo, [definindo um ponto de ruptura](using-breakpoints.md) e iniciando seu aplicativo.

   Por exemplo, a partir do editor de código no Visual Studio, você pode usar o comando **Executar para cursor** para iniciar o aplicativo, depurar conectado e entrar no modo de quebra, em seguida, **F11** para navegar código.

   ![Corra para o cursor e entre no código](../debugger/media/navigate-code-code-stepping.gif "Corra para o cursor e entre no código")

Uma vez no modo de quebra, você pode usar uma variedade de comandos para navegar através de seu código. Durante o modo de pausa, você pode examinar os valores das variáveis para procurar violações ou bugs. Para alguns tipos de projeto, você também pode fazer ajustes no aplicativo enquanto estiver no modo de pausa.

A maioria das janelas de depurador, como as **janelas Modules** e **Watch,** só estão disponíveis enquanto o depurador estiver conectado ao seu aplicativo. Alguns recursos de depurador, como visualizar valores variáveis na janela **Locais** ou avaliar expressões na janela **do relógio,** estão disponíveis apenas enquanto o depurador é pausado (ou seja, no modo de pausa).

> [!NOTE]
> Se você invadir o código que não tem arquivos de origem ou símbolo *(.pdb)* carregados, o depurador exibirá uma página **Não Encontrada ou** **Símbolos Não Encontrados** que podem ajudá-lo a encontrar e carregar os arquivos. Consulte [Especificar símbolo (.pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Se você não puder carregar o símbolo ou os arquivos de origem, você ainda pode depurar as instruções de montagem na janela **Desmontagem.**

## <a name="step-through-code"></a>Percorrer o código

Os comandos da etapa de depurador ajudam você a inspecionar o estado do aplicativo ou a descobrir mais sobre seu fluxo de execução.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Passo para linha de código por linha

Para parar em cada declaração durante a depuração, use **Debug** > **Step Into**ou pressione **F11**.

O depurador passa através de instruções de código, não de linhas físicas. Por exemplo, uma cláusula `if` pode ser escrita em uma linha:

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

No entanto, quando você entra nessa linha, o depurador trata a condição como um passo, e a conseqüência como outro. No exemplo anterior, a condição é verdadeira.

Em uma chamada de função aninhada, a **Depuração Completa** intervém na função aninhada mais profunda. Por exemplo, se você usar **Step Into** em uma chamada como `Func1(Func2())`, o depurador entra na função `Func2`.

>[!TIP]
>À medida que você executa cada linha de código, você pode passar o tempo sobre variáveis para ver seus valores, ou usar as janelas [locais](autos-and-locals-windows.md) e [relógios](watch-and-quickwatch-windows.md) para ver a mudança de valores. Você também pode rastrear visualmente a [pilha de chamadas](how-to-use-the-call-stack-window.md) enquanto entra em funções. (Somente para visual studio enterprise, consulte [métodos de mapa na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Passe pelo código e pule algumas funções

Você pode não se importar com uma função durante a depuração, ou você sabe que funciona, como código de biblioteca bem testado. Você pode usar os seguintes comandos para pular código durante a revisão de código. As funções ainda são executadas, mas o depurador pula sobre elas.

|Comando do teclado|Comando do menu Depurar|Descrição|
|----------------------|------------------|-----------------|
|**F10**|**Depuração Parcial**|Se a linha atual contiver uma chamada de função, **Step Over** executa o código e, em seguida, suspende a execução na primeira linha de código após o retorno da chamada função.|
|**Turno**+**F11**|**Sair**|**Step Out** continua executando código e suspende a execução quando a função atual retorna. O depurador pula a função atual.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Corra para um local ou função específico

Você pode preferir correr diretamente para um local ou função específica quando você sabe exatamente qual código você quer inspecionar, ou você sabe onde você quer começar a depurar.

### <a name="run-to-a-breakpoint-in-code"></a>Corra para um ponto de ruptura no código

Para definir um ponto de ruptura simples em seu código, clique na margem mais à esquerda ao lado da linha de código onde você deseja suspender a execução. Você também pode selecionar a linha e pressionar **F9**, selecione **Debug** > **Toggle Breakpoint**ou clique com o botão direito do mouse e selecione **Breakpoint** > **Insert Breakpoint**. O ponto de partida aparece como um ponto vermelho na margem esquerda ao lado da linha de código. O depurador suspende a execução pouco antes da linha ser executada.

![Defina um ponto de ruptura](../debugger/media/dbg_basics_setbreakpoint.png "Definir um ponto de interrupção")

Os pontos de interrupção no Visual Studio fornecem um conjunto rico de funcionalidades adicionais, como pontos de interrupção e pontos de monitoramento condicionais. Para obter detalhes, consulte [Usando pontos de interrupção](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Execute para um ponto de ruptura de função

Você pode dizer ao depurador para ser executado até que ele atinja uma função especificada. É possível especificar a função por nome ou escolhê-la na pilha de chamadas.

**Para especificar um ponto de ruptura de função por nome**

1. Selecione **Debug** > **New Breakpoint** > **Function Breakpoint Breakpoint**

1. Na caixa de diálogo **'Ponto de ruptura** da nova função', digite o nome da função e selecione seu idioma.

   ![Nova caixa de diálogo ponto de ruptura de função](../debugger/media/dbg_execution_newbreakpoint.png "Novo ponto de ruptura da função")

1. Selecione **OK**.

Se a função estiver sobrecarregada ou em mais de um namespace, você pode escolher a que deseja na janela **Pontos de interrupção.**

![Pontos de interrupção da função sobrecarregada](../debugger/media/dbg_execution_overloadedbreakpoints.png "Pontos de interrupção da função sobrecarregada")

**Para selecionar um ponto de ruptura de função na pilha de chamadas**

1. Durante a depuração, abra a janela **Pilha de** chamadas selecionando **Depurar** > **o Windows** > **Call Stack**.

1. Na janela **Pilha de chamadas,** clique com o botão direito do mouse em uma função e selecione **Executar para cursor**ou **pressione Ctrl**+**F10**.

Para rastrear visualmente a pilha de chamadas, consulte [métodos de mapa na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Corra para um local de cursor

Para correr para o local do cursor, no código-fonte ou na janela **Chamada Pilha,** selecione a linha que deseja quebrar, clique com o botão direito do mouse e selecione **Executar para cursor**ou **pressione Ctrl**+**F10**. Selecionar **Executar para cursor** é como definir um ponto de interrupção temporário.

### <a name="run-to-click"></a>Executar com um Clique

Durante a pausa no depurador, você pode passar o tempo sobre uma declaração no código-fonte ou na janela **Desmontagem** e selecionar a **execução executar para aqui** o ícone do arqueiro verde. O uso **de Executar para clicar** elimina a necessidade de definir um ponto de interrupção temporário.

![Executar com um Clique](../debugger/media/dbg-run-to-click.png "Executar com um Clique")

> [!NOTE]
> **Run to Click** está [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]disponível a partir de .

### <a name="manually-break-into-code"></a>Interromper manualmente o código

Para quebrar a próxima linha de código disponível em um aplicativo em execução, selecione **Debug** > **Break All**ou **pressione Ctrl**+**Alt**+**Break**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Mova o ponteiro para alterar o fluxo de execução

Enquanto o depurador é pausado, uma ponta de seta amarela na margem do código-fonte ou janela **Desmontagem** marca a localização da próxima declaração a ser executada. Você pode alterar a próxima declaração a ser executada movendo esta ponta de seta. Você pode pular uma parte do código ou retornar a uma linha anterior. Mover o ponteiro é útil para situações como pular uma seção de código que contém um bug conhecido.

 ![Mova o ponteiro](../debugger/media/dbg_basics_example3.gif "Mova o ponteiro")

Para alterar a próxima declaração a ser executada, o depurador deve estar no modo de quebra. Na janela código-fonte ou **de desmontagem,** arraste a ponta da seta amarela para uma linha diferente ou clique com o botão direito do mouse na linha que deseja executar a seguir e **selecione Definir próxima declaração**.

O contador do programa salta diretamente para o novo local, e as instruções entre os antigos e os novos pontos de execução não são executadas. No entanto, se você mover o ponto de execução para trás, as instruções de intervenção não são desfeitas.

>[!CAUTION]
>- Mover a instrução seguinte para outra função ou escopo normalmente resulta em danos à pilha de chamadas, causando um erro em tempo de execução ou uma exceção. Se você tentar mover a instrução seguinte para outro escopo, o depurador abrirá uma caixa de diálogo com um aviso e dará uma chance de cancelar a operação.
>- No Visual Basic, você não pode mover a instrução seguinte para outro escopo ou função.
>- No C++ nativo, se você tiver as verificações de tempo de execução ativadas, definir a instrução seguinte poderá fazer com que uma exceção seja gerada quando a execução chegar ao final do método.
>- Quando a opção Editar e Continuar está habilitada, **Definir Próxima Instrução** falha caso você tenha feito edições que Editar e Continuar não pode remapear imediatamente. Isso pode ocorrer, por exemplo, se você editou o código dentro de um bloco catch. Quando isso acontece, uma mensagem de erro diz que a operação não é suportada.
>- No código gerenciado, você não pode mover a próxima declaração se:
>   - A instrução a seguir é um método diferente do que a instrução atual.
>   - A depuração foi iniciada pela depuração just-in-time.
>   - Uma pilha de chamadas desenrola-se está em andamento.
>   - Uma exceção System.StackOverflowException ou System.Threading.ThreadAbortException foi lançada.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Depurar código de não-usuário

Por padrão, o depurador tenta depurar apenas o código do aplicativo, ativando uma configuração chamada *Just My Code*. Para obter mais detalhes sobre como esse recurso funciona para diferentes tipos de projeto e idiomas, e como você pode personalizá-lo, consulte [Just My Code](../debugger/just-my-code.md).

Para olhar o código-quadro, o código da biblioteca de terceiros ou as chamadas do sistema durante a depuração, você pode desativar o Just My Code. Em **Ferramentas** (ou **Depuração)**>**Depuração de** **Opções,** > limpe a caixa de seleção **Habilitar apenas meu código.** Quando Just My Code é desativado, o código de não-usuário aparece nas janelas de depurador e o depurador pode entrar no código de não-usuário.

> [!NOTE]
> Apenas Meu Código não é suportada para projetos de dispositivo.

### <a name="debug-system-code"></a>Código do sistema de depuração

Se você carregou símbolos de depuração para o código do sistema Microsoft e desativou O Meu Código, você pode entrar em uma chamada do sistema da forma que puder em qualquer outra chamada.

Para carregar símbolos da Microsoft, consulte [Configurar locais de símbolos e opções de carregamento](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Para carregar símbolos para um componente específico do sistema:**

1. Enquanto estiver depurando, abra a janela **Módulos** selecionando **Debug** > **Windows** > **Modules**ou pressionando **Ctrl**+**Alt**+**U**.

1. Na janela **Módulos,** você pode dizer quais módulos têm símbolos carregados na coluna **Status do Símbolo.** Clique com o botão direito do mouse no módulo para o que deseja carregar símbolos e selecione **Símbolos de carga**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Intervir em propriedades e operadores no código gerenciado
 O depurador considera propriedades e operadores no código gerenciado por padrão. Na maioria dos casos, isso proporciona uma melhor experiência de depuração. Para habilitar a entrar em propriedades ou operadores, escolha **Opções de depuração** > **Options**. Na página**Geral** **de depuração,** > limpe a caixa de seleção Passo sobre propriedades **e operadores (somente gerenciados).**

## <a name="see-also"></a>Confira também
- [O que é depuração?](../debugger/what-is-debugging.md)
- [Ferramentas e técnicas de depuração](../debugger/write-better-code-with-visual-studio.md)
- [Primeira olhada na depuração](../debugger/debugger-feature-tour.md)
