---
title: Ganchos de alocação e alocações de memória de tempo de execução C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8487972c237b9c2ba6bf2594ffc1df43fa0c63cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702429"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ganchos de alocação e alocações de memória de tempo de execução do C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma restrição muito importante em funções de gancho de alocação é que devem ignorar explicitamente blocos `_CRT_BLOCK` (as alocações de memória feitas internamente por funções da biblioteca em tempo de execução C) se fizerem chamadas às funções da biblioteca em tempo de execução C que alocam a memória interna. Os blocos `_CRT_BLOCK` podem ser ignorados incluindo o código como, por exemplo, o seguinte no início da função de gancho de alocação:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Se seu gancho de alocação não ignorar blocos `_CRT_BLOCK`, qualquer função de biblioteca em tempo de execução C chamada em seu gancho pode interceptar o programa em um loop infinito. Por exemplo, `printf` faz uma alocação interna. Se o seu código de gancho chamar `printf` , a alocação resultante fará com que seu gancho seja chamado novamente, o que chamará **printf** novamente e assim por diante até que a pilha flua. Se você precisar reportar operações de alocação `_CRT_BLOCK`, uma maneira de evitar essa restrição é usar funções de API do Windows, em vez de funções de tempo de execução C, para formatação e saída. Como as APIs do Windows não usam o heap da biblioteca em tempo de execução C, elas não interceptarão seu gancho de alocação em um loop infinito.  
  
 Se você examinar os arquivos de origem da biblioteca em tempo de execução, verá que a função padrão de gancho de alocação, **CrtDefaultAllocHook** (que retorna apenas **TRUE**), está localizada em um arquivo separado, DBGHOOK.C. Se você quiser que o gancho de alocação seja chamado mesmo para as alocações feitas pelo código de inicialização de tempo de execução que é executado antes da função **principal** de seu aplicativo, você poderá substituir essa função padrão por um de seus próprios, em vez de usar [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar a gravação da função do gancho](../debugger/debug-hook-function-writing.md)   
 [Amostra de crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
