---
title: 'Como: Usar a ferramenta localizador | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf3fcf00486ebb8ec54f2d692d483a7f9cf18d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387661"
---
# <a name="how-to-use-the-finder-tool"></a>Como: Usar a ferramenta Localizador
Você pode usar a ferramenta de localização na **localizar janela** caixa de diálogo para exibir propriedades da janela ou mensagens. A ferramenta localizador também poderá localizar janelas filho desabilitadas e distinguir qual janela para realçar se desabilitada a janelas filho se sobrepuserem.

 ![Spy&#43; &#43; caixa de diálogo Localizar janela](../debugger/media/icon_spy--_find.png "Icon_Spy + + Find") ferramenta Descobridora na caixa de diálogo Localizar janela

 A figura acima mostra a caixa de diálogo Localizar janela após a etapa 3 abaixo.

### <a name="to-display-window-properties-or-messages"></a>Para exibir propriedades da janela ou mensagens

1. Organize as janelas para que o Spy + + e a janela de destino estão visíveis.

2. Dos **Spy** menu, escolha **localizar janela**.

    O [caixa de diálogo Localizar janela](../debugger/find-window-dialog-box.md) é aberta.

3. Arraste o **ferramenta Descobridora** sobre a janela de destino.

    À medida que você arrasta a ferramenta, o **localizar janela** caixa de diálogo exibe detalhes sobre a janela selecionada.

   - ou –

     Se você tiver o identificador da janela que você deseja examinar (por exemplo, copiado do depurador), digite-o para o **manipular** caixa de texto.

   > [!TIP]
   > Para reduzir a desordem na tela, selecione a **Spy ocultar** opção. Esta opção oculta a janela principal do Spy + +, deixando apenas o **localizar janela** caixa de diálogo visível na parte superior de seus outros aplicativos. A janela principal do Spy + + é restaurada quando você clica **Okey** ou **Cancelar**, ou quando você desmarca a **ocultar Spy + +** opção.

4. Sob **mostram**, selecione **Properties** ou **mensagens**.

5. Pressione **OK**.

    Se você selecionou **propriedades**, o [caixa de diálogo de propriedades de janela](../debugger/window-properties-dialog-box.md) é aberta. Se você selecionou **mensagens**, um [exibição de mensagens](../debugger/messages-view.md) janela é aberta.

## <a name="see-also"></a>Consulte também
- [Exibições do Spy++](../debugger/spy-increment-views.md)
- [Usando Spy++](../debugger/using-spy-increment.md)
- [Referência a Spy++](../debugger/spy-increment-reference.md)