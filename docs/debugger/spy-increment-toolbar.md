---
title: Barra de ferramentas do Spy + + | Microsoft Docs
description: Entenda os elementos da interface do usuário na barra de ferramentas do Spy + +, que aparece na barra de menus. Para exibir ou ocultar a barra de ferramentas, no menu Exibir, clique em barra de ferramentas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: af6db0f367c73804197ef35d0b3734d68f15a332
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903530"
---
# <a name="spy-toolbar"></a>Barra de ferramentas do Spy++
A barra de ferramentas aparece na barra de menus no Spy + +. Para exibir ou ocultar a barra de ferramentas, no menu **Exibir** , clique em **barra de ferramentas**.

 Os controles a seguir estão disponíveis na barra de ferramentas.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário

|Botão|Efeito|
|------------|------------|
|![Botão do Spy&#43;&#43; Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Exibe um modo de exibição de árvore das janelas e dos controles no sistema. Para obter mais informações, consulte [exibição do Windows](../debugger/windows-view.md).|
|![Botão de processos do Spy&#43;&#43; ](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Exibe um modo de exibição de árvore dos processos no sistema. Para obter mais informações, consulte [exibição de processos](../debugger/processes-view.md).|
|![Botão threads de&#43;&#43; do Spy](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Exibe um modo de exibição de árvore dos threads no sistema. Para obter mais informações, consulte [exibição de threads](../debugger/threads-view.md).|
|![Botão de mensagens do Spy&#43;&#43; ](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Cria uma janela para exibir mensagens de janela e abre a caixa de diálogo **Opções de mensagem** para que você possa selecionar a janela cujas mensagens serão exibidas e também selecionar outras opções. Para obter mais informações, consulte [exibição de mensagens](../debugger/messages-view.md).|
|![Botão iniciar log do Spy&#43;&#43; ](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Inicia o log de mensagens e exibe o fluxo de mensagens. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa. Para obter mais informações, consulte [como: Iniciar e parar a exibição do log de mensagens](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Botão para parar log do Spy&#43;&#43; ](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Interrompe o log de mensagens e a exibição do fluxo de mensagens. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa. Para obter mais informações, consulte [como: Iniciar e parar a exibição do log de mensagens](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Botão Opções de log do Spy&#43;&#43; ](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Exibe a caixa de diálogo [Opções de mensagem](../debugger/message-options-dialog-box.md) . Use essa caixa de diálogo para selecionar os tipos de mensagem e do Windows para exibição. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa.|
|![Botão limpar log do Spy&#43;&#43; ](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|Limpa o conteúdo da janela de **mensagens** ativas. Esse controle está disponível somente quando uma janela de **mensagens** é a janela ativa.|
|![Botão de janela Localizar&#43;&#43; do Spy](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Abre a caixa de diálogo [localizar janela](../debugger/find-window-dialog-box.md) , que permite definir critérios de pesquisa de janela e exibir propriedades ou mensagens. Para obter mais informações, consulte [como: usar a ferramenta Finder](../debugger/how-to-use-the-finder-tool.md).|
|![Botão do Spy&#43;&#43; localizar a primeira janela](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Pesquisa a exibição atual de uma janela, processo, thread ou mensagem correspondente.|
|![Spy&#43;&#43; localizar o botão de próxima janela](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Pesquisa o modo de exibição atual para a próxima janela, processo, thread ou mensagem correspondente. Esse controle (e o comando de menu relacionado) está disponível somente quando há um resultado de pesquisa válido que não é exclusivo. Por exemplo, quando você usa um identificador de janela como o critério de pesquisa na árvore de janela, ele produz resultados exclusivos porque há apenas uma janela na árvore de janela que tem esse identificador; nesta instância, **Localizar próximo** não está disponível.|
|![Botão do Spy&#43;&#43; localizar a janela anterior](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Pesquisa o modo de exibição atual da janela, processo, thread ou mensagem correspondente anterior. Esse controle (e o comando de menu relacionado) está disponível somente quando há um resultado de pesquisa válido que não é exclusivo. Por exemplo, quando você usa um identificador de janela como o critério de pesquisa na árvore de janela, ele produz resultados exclusivos porque há apenas uma janela na árvore de janela que tem esse identificador; nesta instância, **Localizar anterior** não está disponível.|
|![Botão Gerenciador de propriedades do Spy&#43;&#43; ](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Exibe as propriedades da janela selecionada no modo de exibição do Windows.|
|![Botão de atualização do Spy&#43;&#43; ](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Atualiza as exibições do sistema.|

## <a name="see-also"></a>Confira também
- [Usando Spy++](../debugger/using-spy-increment.md)
- [Exibições do Spy++](../debugger/spy-increment-views.md)
- [Referência de Spy++](../debugger/spy-increment-reference.md)