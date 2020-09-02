---
title: Barra de ferramentas do Spy + + | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a96a5765c98bf8e7d1c600fbd47478a88fa7175d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154062"
---
# <a name="spy-toolbar"></a>Barra de ferramentas do Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A barra de ferramentas aparece na barra de menus no Spy + +. Para exibir ou ocultar a barra de ferramentas, no menu **Exibir** , clique em **barra de ferramentas**.  
  
 Os controles a seguir estão disponíveis na barra de ferramentas.  
  
## <a name="uielement-list"></a>Lista de elementos de interface do usuário  
  
|Botão|Efeito|  
|------------|------------|  
|![Botão do Spy&#43;&#43; Windows](../debugger/media/icon-spy-windows.gif "Icon_Spy + + _Windows")|Exibe um modo de exibição de árvore das janelas e dos controles no sistema. Para obter mais informações, consulte [exibição do Windows](../debugger/windows-view.md).|  
|![Botão de processos do Spy&#43;&#43; ](../debugger/media/icon-spy-processes.gif "Icon_Spy + + _Processes")|Exibe um modo de exibição de árvore dos processos no sistema. Para obter mais informações, consulte [exibição de processos](../debugger/processes-view.md).|  
|![Botão threads de&#43;&#43; do Spy](../debugger/media/icon-spy-threads.gif "Icon_Spy + + _Threads")|Exibe um modo de exibição de árvore dos threads no sistema. Para obter mais informações, consulte [exibição de threads](../debugger/threads-view.md).|  
|![Botão de mensagens do Spy&#43;&#43; ](../debugger/media/icon-spy-messages.gif "Icon_Spy + + _Messages")|Cria uma janela para exibir mensagens de janela e abre a caixa de diálogo **Opções de mensagem** para que você possa selecionar a janela cujas mensagens serão exibidas e também selecionar outras opções. Para obter mais informações, consulte [exibição de mensagens](../debugger/messages-view.md).|  
|![Botão iniciar log do Spy&#43;&#43; ](../debugger/media/icon-spy-startlog.gif "Icon_Spy + + _StartLog")|Inicia o log de mensagens e exibe o fluxo de mensagens. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa. Para obter mais informações, consulte [como: Iniciar e parar a exibição do log de mensagens](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Botão para parar log do Spy&#43;&#43; ](../debugger/media/icon-spy-stoplog.gif "Icon_Spy + + _StopLog")|Interrompe o log de mensagens e a exibição do fluxo de mensagens. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa. Para obter mais informações, consulte [como: Iniciar e parar a exibição do log de mensagens](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Botão Opções de log do Spy&#43;&#43; ](../debugger/media/icon-spy-logoptions.gif "Icon_Spy + + _LogOptions")|Exibe a caixa de diálogo [Opções de mensagem](../debugger/message-options-dialog-box.md) . Use essa caixa de diálogo para selecionar os tipos de mensagem e do Windows para exibição. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa.|  
|![Botão limpar log do Spy&#43;&#43; ](../debugger/media/spy-clearlog.gif "Spy + + _ClearLog")|Limpa o conteúdo da janela de **mensagens** ativas. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa.|  
|![Botão de janela Localizar&#43;&#43; do Spy](../debugger/media/icon-spy-findwindow.gif "Icon_Spy + + _FindWindow")|Abre a caixa de diálogo [localizar janela](../debugger/find-window-dialog-box.md) , que permite definir critérios de pesquisa de janela e exibir propriedades ou mensagens. Para obter mais informações, consulte [como: usar a ferramenta Finder](../debugger/how-to-use-the-finder-tool.md).|  
|![Botão do Spy&#43;&#43; localizar a primeira janela](../debugger/media/icon-spy-window.gif "Icon_Spy + + _Window")|Pesquisa a exibição atual de uma janela, processo, thread ou mensagem correspondente.|  
|![Spy&#43;&#43; localizar o botão de próxima janela](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy + + _NextWindow")|Pesquisa o modo de exibição atual para a próxima janela, processo, thread ou mensagem correspondente. Esse controle (e o comando de menu relacionado) está disponível somente quando há um resultado de pesquisa válido que não é exclusivo. Por exemplo, quando você usa um identificador de janela como o critério de pesquisa na árvore de janela, ele produz resultados exclusivos porque há apenas uma janela na árvore de janela que tem esse identificador; nesta instância, **Localizar próximo** não está disponível.|  
|![Botão do Spy&#43;&#43; localizar a janela anterior](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy + + _PrevWindow")|Pesquisa o modo de exibição atual da janela, processo, thread ou mensagem correspondente anterior. Esse controle (e o comando de menu relacionado) está disponível somente quando há um resultado de pesquisa válido que não é exclusivo. Por exemplo, quando você usa um identificador de janela como o critério de pesquisa na árvore de janela, ele produz resultados exclusivos porque há apenas uma janela na árvore de janela que tem esse identificador; nesta instância, **Localizar anterior** não está disponível.|  
|![Botão Gerenciador de propriedades do Spy&#43;&#43; ](../debugger/media/icon-spy-propexp.gif "Icon_Spy + + _PropExp")|Exibe as propriedades da janela selecionada no modo de exibição do Windows.|  
|![Botão de atualização do Spy&#43;&#43; ](../debugger/media/icon-spy-refresh.gif "Icon_Spy + + _Refresh")|Atualiza as exibições do sistema.|  
  
## <a name="see-also"></a>Consulte Também  
 [Usando o Spy + +](../debugger/using-spy-increment.md)   
 [Modos de exibição do Spy + +](../debugger/spy-increment-views.md)   
 [Referência de Spy++](../debugger/spy-increment-reference.md)
