---
title: 'Como: Pesquisar um thread no modo de exibição de threads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5974bc962faf439af8de5d50bf51bad3d824647
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838487"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Como procurar um thread na exibição de threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode pesquisar um thread específico na exibição Threads usando sua ID de thread ou cadeia de caracteres de módulo como critérios de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrarão os atributos do thread selecionado na árvore de thread.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Para procurar um thread na exibição threads  
  
1. Organize suas janelas para que o Spy + + e uma janela de [exibição de threads](../debugger/threads-view.md) ativas fiquem visíveis.  
  
2. No menu **Pesquisar** , escolha **Localizar thread**.  
  
    A [caixa de diálogo pesquisa de threads](../debugger/thread-search-dialog-box.md) é aberta.  
  
3. Digite a ID do thread ou uma cadeia de caracteres do módulo como critérios de pesquisa.  
  
4. Desmarque os campos para os quais você não deseja especificar valores.  
  
   > [!TIP]
   > Para localizar todos os threads pertencentes a um módulo, desmarque a caixa de texto **thread** e digite o nome do módulo na caixa **módulo** . Em seguida, use **Localizar próximo** para continuar a procurar por threads.  
  
5. Escolha para **cima** ou para **baixo** na direção inicial da pesquisa.  
  
6. Clique em **OK**.  
  
   Se um thread correspondente for encontrado, ele será realçado na janela exibição de threads.
