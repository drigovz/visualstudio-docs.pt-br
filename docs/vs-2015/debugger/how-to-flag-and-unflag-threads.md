---
title: 'Como: Sinalizar e remover sinalização de Threads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: be6ebe9e2031b24442f368b626d53b15a043023c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922127"
---
# <a name="how-to-flag-and-unflag-threads"></a>Como: Sinalizar e remover sinalização de threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode sinalizar um thread que você deseja dar atenção especial marcando-o com um ícone na **Threads**, **pilhas paralelas**, **inspeção paralela**, e **GPU Threads** windows. Esse ícone pode ajudá-lo e a outros a distinguir threads sinalizados de outros threads.  
  
 Threads sinalizados também recebem tratamento especial na **Thread** lista os **local de depuração** barra de ferramentas. Esta lista pode mostrar todos os threads ou apenas os sinalizados. Quando você sinaliza um thread, o **Thread** lista alterna automaticamente para mostrar somente threads sinalizados, mas você pode alternar para mostrar todos os threads conforme apropriado.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Para sinalizar ou desmarcar a sinalização de um thread usando a janela de threads  
  
-   No **Threads** janela, localize o thread que você está interessado e clique no ícone de sinalizador para marcar ou desmarcar o sinalizador.  
  
### <a name="to-unflag-all-threads"></a>Para remover a sinalização de todos os threads  
  
-   Na janela **Threads**, clique com o botão direito do mouse em qualquer thread e clique em **Remover Sinalização de Todos os Threads**.  
  
### <a name="to-display-only-flagged-threads"></a>Para exibir somente threads sinalizados  
  
-   Escolha o botão de sinalizador na janela de depuração.  
  
### <a name="to-flag-just-my-code"></a>Para sinalizar apenas meu código  
  
1.  Na barra de ferramentas na parte superior da janela **Threads**, clique no ícone do sinalizador.  
  
2.  Na lista suspensa, clique em **Sinalizar Apenas Meu Código**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Para sinalizar os threads que estão associados com os módulos selecionados  
  
1.  Na barra de ferramentas da janela **Threads**, clique no ícone do sinalizador.  
  
2.  Na lista suspensa, clique em **Sinalizar Seleção de Módulo Personalizada**.  
  
3.  Na caixa de diálogo **Selecionar Módulos**, selecione os módulos desejados.  
  
4.  (Opcional) Na caixa **Pesquisar**, digite uma cadeia de caracteres para pesquisar módulos específicos.  
  
5.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multi-threaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Passo a passo: Como depurar um aplicativo multi-threaded](../debugger/walkthrough-debugging-a-multithreaded-application.md)
