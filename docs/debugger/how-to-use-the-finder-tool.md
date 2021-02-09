---
title: Usar a ferramenta Finder | Microsoft Docs
description: Use a ferramenta localizador na caixa de diálogo localizar janela da ferramenta Spy + + para exibir as propriedades ou as mensagens da janela durante uma sessão de depuração.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d48e9b580d25b521721fafa7dc475bdbe3532656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912226"
---
# <a name="how-to-use-the-finder-tool"></a>Como usar a ferramenta Localizador
Você pode usar a ferramenta Finder na caixa de diálogo **localizar janela** para exibir as propriedades ou as mensagens da janela. A ferramenta de localizador também pode localizar janelas filhas desabilitadas e discernir qual janela destacar se a sobreposição de janelas filho desabilitada.

 ![Caixa de diálogo janela localizar&#43;&#43; do Spy](../debugger/media/icon_spy--_find.png "Icon_Spy + + _Find") Ferramenta de localizador na caixa de diálogo localizar janela

 A figura acima mostra a caixa de diálogo localizar janela após a etapa 3 abaixo.

### <a name="to-display-window-properties-or-messages"></a>Para exibir propriedades ou mensagens da janela

1. Organize suas janelas para que o Spy + + e a janela de destino fiquem visíveis.

2. No menu do **Spy** , escolha **localizar janela**.

    A [caixa de diálogo localizar janela](../debugger/find-window-dialog-box.md) é aberta.

3. Arraste a **ferramenta localizador** sobre a janela de destino.

    À medida que você arrasta a ferramenta, a caixa de diálogo **localizar janela** exibe detalhes na janela selecionada.

   - ou –

     Se você tiver o identificador da janela que deseja examinar (por exemplo, copiado do depurador), digite-o na caixa de texto **identificador** .

   > [!TIP]
   > Para reduzir a desordem na tela, selecione a opção **ocultar Spy** . Essa opção oculta a janela principal do Spy + +, deixando apenas a caixa de diálogo **localizar janela** visível sobre seus outros aplicativos. A janela principal Spy + + é restaurada quando você clica em **OK** ou em **Cancelar**, ou quando você desmarca a opção **ocultar Spy + +** .

4. Em **Mostrar**, selecione **Propriedades** ou **mensagens**.

5. Pressione **OK**.

    Se você selecionou **Propriedades**, a [caixa de diálogo Propriedades da janela](../debugger/window-properties-dialog-box.md) será aberta. Se você selecionou **mensagens**, uma janela [exibição de mensagens](../debugger/messages-view.md) será aberta.

## <a name="see-also"></a>Consulte também
- [Exibições do Spy++](../debugger/spy-increment-views.md)
- [Usando Spy++](../debugger/using-spy-increment.md)
- [Referência de Spy++](../debugger/spy-increment-reference.md)