---
title: Ganchos de alocação e alocações de memória de tempo de execução C | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f7f81abd82857b3d9ed2161a6923a79b614bf5a
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742388"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ganchos de alocação e alocações de memória de tempo de execução do C
Uma restrição muito importante em funções de gancho de alocação é que eles devem ignorar explicitamente `_CRT_BLOCK` blocos. Esses blocos são as alocações de memória feitas internamente por funções da biblioteca de tempo de execução C se eles fizerem chamadas às funções de biblioteca de tempo de execução C que alocam memória interna. Você pode ignorar `_CRT_BLOCK` função de gancho de blocos, incluindo o código a seguir no início de sua alocação:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Se seu gancho de alocação não ignorar `_CRT_BLOCK` bloqueia, em seguida, qualquer função de biblioteca de tempo de execução C chamada em seu gancho pode interceptar o programa em um loop infinito. Por exemplo, `printf` faz uma alocação interna. Se o código de gancho chamar `printf`, a alocação resultante fará o gancho ser chamado novamente, que chamará **printf** novamente e assim por diante, até o estouro de pilha. Se você precisar reportar operações de alocação `_CRT_BLOCK`, uma maneira de evitar essa restrição é usar funções de API do Windows, em vez de funções de tempo de execução C, para formatação e saída. Como as APIs do Windows não usam o heap da biblioteca em tempo de execução C, eles não interceptar o seu gancho de alocação em um loop infinito.

Se você examinar os arquivos de origem da biblioteca em tempo de execução, verá que a função padrão de gancho de alocação, **CrtDefaultAllocHook** (que retorna apenas **TRUE**), está localizada em um arquivo separado, DBGHOOK.C. Se você quiser que o gancho de alocação seja chamado mesmo para as alocações feitas pelo código de inicialização de tempo de execução que é executado antes da função **principal** de seu aplicativo, você poderá substituir essa função padrão por um de seus próprios, em vez de usar [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Consulte também
[Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)
