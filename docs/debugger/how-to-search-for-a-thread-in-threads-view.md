---
title: Pesquisar um thread no modo de exibição de threads | Microsoft Docs
description: Procure um thread específico na exibição threads da ferramenta Spy + + usando sua ID de thread ou cadeia de caracteres de módulo como critérios de pesquisa ao depurar no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92864c9d3c66a7547ef52a2694f6307d57a43304
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148527"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Como procurar um thread na exibição de threads
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