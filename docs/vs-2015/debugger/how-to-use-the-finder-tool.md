---
title: 'Como: usar a ferramenta Finder | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00535fd336f504afcebdd24a4d009a10f7f6ff33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838554"
---
# <a name="how-to-use-the-finder-tool"></a>Como usar a ferramenta Localizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar a ferramenta Finder na caixa de diálogo **localizar janela** para exibir as propriedades ou as mensagens da janela. A ferramenta de localizador também pode localizar janelas filhas desabilitadas e discernir qual janela destacar se a sobreposição de janelas filho desabilitada.  
  
 ![Caixa de diálogo janela Localizar&#43;&#43; do Spy](../debugger/media/icon-spy-find.png "Icon_Spy + + _Find")  
Ferramenta de localizador na caixa de diálogo localizar janela  
  
 A figura acima mostra a caixa de diálogo localizar janela após a etapa 3 abaixo.  
  
### <a name="to-display-window-properties-or-messages"></a>Para exibir propriedades ou mensagens da janela  
  
1. Organize suas janelas para que o Spy + + e a janela de destino fiquem visíveis.  
  
2. No menu do **Spy** , escolha **localizar janela**.  
  
     A [caixa de diálogo localizar janela](../debugger/find-window-dialog-box.md) é aberta.  
  
3. Arraste a **ferramenta localizador** sobre a janela de destino.  
  
     À medida que você arrasta a ferramenta, a caixa de diálogo **localizar janela** exibe detalhes na janela selecionada.  
  
     – ou –  
  
     Se você tiver o identificador da janela que deseja examinar (por exemplo, copiado do depurador), digite-o na caixa de texto **identificador** .  
  
    > [!TIP]
    > Para reduzir a desordem na tela, selecione a opção **ocultar Spy** . Essa opção oculta a janela principal do Spy + +, deixando apenas a caixa de diálogo **localizar janela** visível sobre seus outros aplicativos. A janela principal Spy + + é restaurada quando você clica em **OK** ou em **Cancelar**, ou quando você desmarca a opção **ocultar Spy + +** .  
  
4. Em **Mostrar**, selecione **Propriedades** ou **mensagens**.  
  
5. Pressione **OK**.  
  
     Se você selecionou **Propriedades**, a [caixa de diálogo Propriedades da janela](../debugger/window-properties-dialog-box.md) será aberta. Se você selecionou **mensagens**, uma janela [exibição de mensagens](../debugger/messages-view.md) será aberta.  
  
## <a name="see-also"></a>Consulte Também  
 [Modos de exibição do Spy + +](../debugger/spy-increment-views.md)   
 [Usando o Spy + +](../debugger/using-spy-increment.md)   
 [Referência de Spy++](../debugger/spy-increment-reference.md)
