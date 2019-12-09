---
title: 'Como: Pesquisar por um Thread na exibição de Threads | Microsoft Docs'
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
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64827350"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Como: Pesquise um thread na exibição de threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode procurar um segmento específico na exibição de Threads por meio de sua cadeia de caracteres de ID ou o módulo de thread como critérios de pesquisa. Você também pode especificar a direção inicial da pesquisa. Os campos na caixa de diálogo mostrará os atributos de thread selecionado na árvore de thread.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Para pesquisar por um thread na exibição de Threads  
  
1. Organizar as janelas assim que Spy + + e um ativo [exibição de Threads](../debugger/threads-view.md) janela são visíveis.  
  
2. Dos **pesquisa** menu, escolha **localizar Thread**.  
  
    O [caixa de diálogo de pesquisa de Thread](../debugger/thread-search-dialog-box.md) é aberta.  
  
3. Como critérios de pesquisa, digite a ID do thread ou uma cadeia de caracteres do módulo.  
  
4. Limpe todos os campos para o qual você deseja especificar valores.  
  
   > [!TIP]
   > Para localizar todos os threads pertencentes a um módulo, desmarque a **Thread** nome de caixa de texto e o tipo de módulo na **módulo** caixa. Em seguida, use **Localizar próximo** para continuar a pesquisa de threads.  
  
5. Escolher **para cima** ou **para baixo** para a direção inicial da pesquisa.  
  
6. Clique em **OK**.  
  
   Se um thread correspondente for encontrado, ele é realçado na janela de exibição de Threads.
