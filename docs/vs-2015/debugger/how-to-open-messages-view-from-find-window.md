---
title: 'Como: Abrir modo de exibição de mensagens da janela Localizar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee29135e659eff7e4965b6b1fb0d24de2c2e90cc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078728"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Como: Abrir a exibição de mensagens de Localizar janela
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Talvez seja conveniente usar o **localizar janela** caixa de diálogo para selecionar uma janela de destino e, em seguida, abrir um modo de exibição de mensagens dessa janela.  
  
### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Para abrir uma janela de exibição de mensagens usando a caixa de diálogo Localizar janela  
  
1. Organize as janelas para que o Spy + + e a janela de destino estão visíveis.  
  
2. Dos **Spy** menu, escolha **localizar janela**.  
  
     O [caixa de diálogo Localizar janela](../debugger/find-window-dialog-box.md) é aberta.  
  
3. Dos **Windows** guia, arraste a **ferramenta Descobridora** sobre a janela de destino. À medida que você arrasta a ferramenta, o **localizar janela** caixa de diálogo exibe detalhes sobre a janela selecionada.  
  
     – ou –  
  
     Se você tiver o identificador da janela que você deseja examinar (por exemplo, copiado do depurador), você pode digitá-lo na **manipular** caixa de texto.  
  
4. Sob **mostram**, selecione **mensagens**.  
  
5. Pressione **OK**.  
  
     Um espaço em branco [exibição de mensagens](../debugger/messages-view.md) janela é aberta e um **mensagens** menu é adicionado à barra de ferramentas Spy + +.  
  
6. Dos **mensagens** menu, escolha **opções de log**.  
  
     O [caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md) é aberta.  
  
7. Selecione as opções para as mensagens que você deseja exibir.  
  
8. Pressione **Okey** para começar a mensagens de log.  
  
     Dependendo das opções selecionadas, as mensagens inicia o streaming para a janela de exibição de mensagens ativa.  
  
9. Quando você ter mensagens suficientes, escolha **parar log** da **mensagens** menu.
