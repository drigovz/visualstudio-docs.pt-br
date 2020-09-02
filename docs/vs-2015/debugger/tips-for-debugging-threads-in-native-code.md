---
title: Dicas para depurar threads em código nativo | Microsoft Docs
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
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684865"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Dicas para threads de depuração no código nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veja algumas dicas que você pode usar durante a depuração de threads em código nativo:  
  
- Você pode exibir o conteúdo do bloco de informações sobre o thread digitando `@TIB` na janela **Inspeção** ou na caixa de diálogo **QuickWatch**.  
  
- Para exibir o último código de erro do thread atual, digite `@Err` na janela **Inspeção** ou na caixa de diálogo **QuickWatch**.  
  
- As funções das bibliotecas em tempo de execução do C (CRT) podem ser úteis para depurar um aplicativo multithreaded. Para obter mais informações, consulte [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar aplicativos multissegmentados](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)
