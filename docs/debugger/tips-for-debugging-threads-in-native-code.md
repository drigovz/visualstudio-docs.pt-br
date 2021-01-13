---
title: Dicas para depurar threads em código nativo | Microsoft Docs
description: Leia uma lista de dicas para depurar threads em código nativo se você estiver Depurando aplicativos multithread no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9249e1527a7dd2ae720ab575b1d443c10b85376e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150048"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Dicas para threads de depuração no código nativo
Veja algumas dicas que você pode usar durante a depuração de threads em código nativo:

- Você pode exibir o conteúdo do bloco de informações sobre o thread digitando `@TIB` na janela **Inspeção** ou na caixa de diálogo **QuickWatch**.

- Para exibir o último código de erro do thread atual, digite `@Err` na janela **Inspeção** ou na caixa de diálogo **QuickWatch**.

- As funções das bibliotecas em tempo de execução do C (CRT) podem ser úteis para depurar um aplicativo multithreaded. Para obter mais informações, consulte [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Confira também
- [Depurar aplicativos multissegmentados](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)