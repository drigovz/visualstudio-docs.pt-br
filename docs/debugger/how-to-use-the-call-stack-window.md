---
title: Exibir a pilha de chamadas no depurador do Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/29/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 264aeeeaac47e30eb08b4320443da15ea48a8601
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257232"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Exibir a pilha de chamadas e usar a janela pilha de chamadas no depurador

Usando o **pilha de chamadas** janela, você pode exibir as chamadas de função ou procedimento que estão atualmente na pilha. A janela **Pilha de Chamadas** mostra a ordem em que os métodos e as funções são chamados. A pilha de chamadas é uma boa maneira de examinar e entender o fluxo de execução de um aplicativo.
  
Quando [símbolos de depuração](#bkmk_symbols) não estão disponíveis para a parte de uma pilha de chamadas, o **pilha de chamadas** janela pode não ser capaz de exibir as informações corretas para essa parte da pilha de chamadas, exibindo em vez disso:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> A janela **Pilha de Chamadas** é semelhante à perspectiva de Depuração em alguns IDEs, como o Eclipse. 
> 
> [!NOTE]
>  As caixas de diálogo e os comandos de menu vistos podem ser diferentes daqueles descritos aqui, dependendo da edição ou das configurações ativas. Para alterar suas configurações, selecione **Import and Export Settings** sobre o **ferramentas** menu.  Ver [Personalizando o IDE](../ide/personalizing-the-visual-studio-ide.md).
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Exibir a pilha de chamadas no depurador 
  
- Durante a depuração, o **Debug** menu, selecione **Windows > pilha de chamadas**.

  ![Janela pilha de chamadas](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Uma seta amarela identifica o quadro de pilha onde o ponteiro de execução está localizado atualmente. Por padrão, as informações deste quadro de pilhas aparecem na fonte de **Locals**, **Autos**, **Assista**, e **desmontagem** windows. Para alterar o contexto do depurador para outro quadro na pilha, [alternar para outro quadro de pilha](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Exibir o código de não usuário na janela pilha de chamadas  
  
-   Clique com botão direito do **pilha de chamadas** janela e selecione **Mostrar código externo**.

Código de não usuário é qualquer código que não é mostrado quando [Just My Code](../debugger/just-my-code.md) está habilitado. No código gerenciado, os quadros de código não-usuário ficam ocultos por padrão. A notação a seguir será exibida no lugar os quadros de código não-usuário:  
  
`[<External Code>]`
  
## <a name="bkmk_switch"></a> Alternar para outro quadro de pilha (alterar o contexto do depurador)
  
1.  No **pilha de chamadas** janela, o botão direito do mouse a pilha de quadro cujos código e os dados que você deseja exibir.

    Ou, você pode clicar duas vezes em um quadro do **pilha de chamadas** janela para alternar para quadro. 
  
2.  Selecione **alternar para quadro**.  
  
     Uma seta verde com uma parte final encaracolada aparece ao lado do quadro de pilha que você selecionou. O ponteiro de execução permanece no quadro original, que ainda está marcado com a seta amarela. Se você selecionar **etapa** ou **continuar** do **depurar** menu, a execução continuará no quadro original, não no quadro selecionado.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Exibir o código-fonte para uma função na pilha de chamadas  
  
-   No **pilha de chamadas** janela, o botão direito do mouse na função cujo código-fonte código que você deseja ver e selecione **ir para código-fonte**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Executar uma função específica da janela pilha de chamadas  
  
-  No **pilha de chamadas** janela, selecione a função, clique com botão direito e, em seguida, escolha **executar até o Cursor**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Defina um ponto de interrupção no ponto de saída de uma chamada de função  
  
-   Ver [defina um ponto de interrupção em uma função de pilha de chamada](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Exibe chamadas para ou de outro thread  
  
-   Clique com botão direito do **pilha de chamadas** janela e selecione **incluem chamadas para / de outros Threads**.   
  
## <a name="visually-trace-the-call-stack"></a>Rastrear visualmente a pilha de chamadas  

No Visual Studio Enterprise (somente), você pode exibir mapas de código para a pilha de chamadas durante a depuração.

- No **pilha de chamadas** janela, abra o menu de atalho. Escolher **Mostrar pilha de chamadas no mapa de códigos** (**Ctrl** + **Shift** + **`**).  
  
    Para obter mais informações, consulte [mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Mostrar pilha de chamadas no mapa de códigos](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Exibir o código de desmontagem para uma função na pilha de chamadas (C#, C++, Visual Basic, F#) 
  
-   No **pilha de chamadas** janela, o botão direito do mouse a função cujo código de desmontagem você deseja ver e selecione **ir para desmontagem**.    

## <a name="change-the-optional-information-displayed"></a>Alterar as informações opcionais exibidas  
  
-   Clique com botão direito no **pilha de chamadas** janela e defina ou desmarque **mostram \<**  _as informações que você deseja_ **>**.  
  
## <a name="bkmk_symbols"></a> Carregar símbolos para um módulo (C#, C++, Visual Basic, F#)

No **pilha de chamadas** janela, você pode carregar símbolos de depuração para o código que não tem símbolos carregados atualmente. Esses símbolos podem ser do .NET Framework ou símbolos de sistema baixados do servidores de símbolo públicos da Microsoft ou símbolos em um caminho de símbolo no computador que você está depurando.  
  
Ver [especificar arquivos de símbolo (. PDB) e código-fonte](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
### <a name="to-load-symbols"></a>Para carregar símbolos  
  
1.  No **pilha de chamadas** janela, o botão direito do mouse quadro da pilha para o qual os símbolos não são carregados. O quadro ficará esmaecido.  
  
2.  Aponte para **Load Symbols** e, em seguida, selecione **servidores de símbolo Microsoft** (se disponível), ou navegue até o caminho do símbolo.  
  
### <a name="to-set-the-symbol-path"></a>Para definir o caminho do símbolo  
  
1.  No **pilha de chamadas** janela, escolha **configurações de símbolo** no menu de atalho.  
  
     O **opções** caixa de diálogo é aberta e o **símbolos** página é exibida.  
  
2.  Selecione **configurações de símbolo**.  
  
3.  No **opções** caixa de diálogo, clique no ícone de pasta.  
  
     No **locais de arquivo (. PDB) de símbolo** caixa, será exibido um cursor.  
  
4.  Insira um nome de caminho de diretório para o local do símbolo no computador que você está depurando. Para depuração local e remota, esse é um caminho no computador local.
  
5.  Selecione **Okey** para fechar o **opções** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Código misto e informações ausentes na janela Pilha de Chamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar arquivos de símbolo (. PDB) e código-fonte](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)