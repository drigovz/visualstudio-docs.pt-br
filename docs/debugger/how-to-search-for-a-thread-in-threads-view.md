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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85d82897144a0ed366d95dfa590a09224a875f55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845055"
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