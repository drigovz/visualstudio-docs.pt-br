---
title: 'Como: usar a janela pilha de chamadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697482"
---
# <a name="how-to-use-the-call-stack-window"></a>Como usar a janela Pilha de Chamadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao usar a janela **Pilha de Chamadas**, você pode exibir chamadas de função ou procedimento que estão na pilha atualmente.  
  
 A janela **pilha de chamadas** exibe o nome de cada função e a linguagem de programação na qual ele está escrito. O nome da função ou do procedimento pode ser acompanhado de informações opcionais, como o nome do módulo, o número da linha e os nomes de parâmetro, tipos e valores. A exibição dessas informações opcionais pode ser ativada ou desativada.  
  
 Uma seta amarela identifica o quadro de pilha onde o ponteiro de execução está localizado atualmente. Por padrão, esse é o quadro cujas informações aparecem na fonte, **desmontagem**, **locais**, **inspecionar**e janelas **automáticas** . Se você quiser alterar o contexto para outro quadro na pilha, poderá fazer isso na janela **pilha de chamadas** .  
  
 Quando os símbolos de depuração não estão disponíveis para parte de uma pilha de chamadas, a janela **pilha de chamadas** pode não ser capaz de exibir as informações corretas para essa parte da pilha de chamadas. A notação a seguir aparece:  
  
 [Os quadros abaixo podem estar incorretos e/ou ausentes, nenhum símbolo carregado para name.dll]  
  
 Em código gerenciado, por padrão. a janela **pilha de chamadas** oculta informações de código que não são de usuário. Aparecerá as notações a seguir em vez das informações ocultas:  
  
 **[\<External Code>]**  
  
 Um código que não seja do usuário é qualquer código que não seja "Meu Código". Você pode optar por exibir informações da pilha de chamadas para o código que não é do usuário usando o menu de atalho.  
  
 Ao usar o menu de atalho, você pode escolher se exibe chamadas entre threads.  
  
> [!NOTE]
> As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas. Para alterar as configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Para exibir a janela Pilha de chamadas no modo de interrupção ou no modo de execução  
  
- No menu **depurar** , selecione **Windows** e, em seguida, clique em **pilha de chamadas**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Para alterar as informações opcionais exibidas  
  
- Clique com o botão direito do mouse na janela **pilha de chamadas** e defina ou desmarque **Mostrar \<**_the information that you want_**> **.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Para exibir quadros de código de não usuário na janela Pilha de chamadas  
  
- Clique com o botão direito do mouse na janela **Pilha de Chamadas** e selecione **Mostrar Código Externo**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Para alternar para outro registro de ativação  
  
1. Na janela **pilha de chamadas** , clique com o botão direito do mouse no quadro cujo código e dados você deseja exibir.  
  
2. Selecione **Alternar para Quadro**.  
  
     Uma seta verde com uma parte final encaracolada aparece ao lado do quadro que você selecionou. O ponteiro de execução permanece no quadro original, que ainda está marcado com a seta amarela. Se você selecionar **Etapa** ou **Continuar** no menu **Depurar**, a execução continuará no quadro original, não no quadro selecionado.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Para exibir chamadas para ou de outro segmento  
  
- Clique com o botão direito do mouse na janela **Pilha de Chamadas** e selecione **Incluir chamadas para/de outros threads**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Para exibir o código-fonte em uma função na pilha de chamadas  
  
- Na janela **Pilha de Chamadas**, clique com o botão direito do mouse na função cujo código-fonte você deseja ver e selecione **Ir para Código-Fonte**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Para rastrear visualmente a pilha de chamadas  
  
1. Na janela **Pilha de Chamadas**, abra o menu de atalho. Escolha **Mostrar pilha de chamadas no mapa de códigos**. (Teclado: **Ctrl**  +  **Shift**  +  **`** )  
  
     Consulte [métodos de mapeamento na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Para exibir o código de desmontagem de uma função na pilha de chamadas  
  
- Na janela **Pilha de Chamadas**, clique com o botão direito do mouse na função cujo código de desmontagem você deseja ver e selecione **Ir para Desmontagem**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Para executar em uma função específica da janela de pilha de chamadas  
  
- Na janela **pilha de chamadas** , selecione a função, clique com o botão direito do mouse e escolha **executar até o cursor**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Para definir um ponto de interrupção no ponto de saída de uma chamada de função  
  
- Consulte [definir um ponto de interrupção em uma função de pilha de chamadas](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Para carregar símbolos para um módulo  
  
- Na janela **pilha de chamadas** , clique com o botão direito do mouse no quadro que mostra o módulo cujos símbolos você deseja recarregar e selecione **carregar símbolos**.  
  
## <a name="loading-symbols"></a>Carregando símbolos  
 Na janela **Pilha de Chamadas**, você pode carregar símbolos de depuração para o código que atualmente não tem símbolos carregados. Esses símbolos podem ser símbolos do .NET Framework ou do sistema baixados dos servidores públicos de símbolo da Microsoft ou de símbolos em um caminho de símbolo no computador que você está depurando.  
  
 Confira [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Para carregar símbolos  
  
1. Na janela **pilha de chamadas** , clique com o botão direito do mouse no quadro para o qual os símbolos não estão carregados. O quadro ficará esmaecido.  
  
2. Aponte para **carregar símbolos de** e clique em **servidores de símbolos** ou **caminho de símbolo**da Microsoft.  
  
#### <a name="to-set-the-symbol-path"></a>Para definir o caminho do símbolo  
  
1. Na janela **Pilha de Chamadas**, escolha **Configurações de Símbolo** no menu de atalho.  
  
     A caixa de diálogo **Opções** abre e a página **Símbolos** é exibida.  
  
2. Clique em **configurações de símbolo**.  
  
3. Na caixa de diálogo **Opções**, clique no ícone da Pasta.  
  
     Na caixa **Locais do arquivo de símbolo (.pdb)**, um cursor será exibido.  
  
4. Digite um nome de caminho de diretório no local do símbolo no computador que você está depurando. Para depuração local, este é o computador local. Para depuração remota, é o computador remoto.  
  
5. Clique em **OK** para fechar a caixa de diálogo **Opções** .  
  
## <a name="see-also"></a>Consulte Também  
 [Código misto e informações ausentes na janela pilha de chamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Como alterar o formato numérico das janelas do depurador](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar o símbolo (. pdb) e os arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)
