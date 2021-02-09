---
title: Ganchos de alocação e alocações de memória de tempo de execução do C
description: Entenda os ganchos de alocação e as alocações de memória de tempo de execução C na depuração do Visual Studio. As funções de gancho de alocação devem ignorar explicitamente os blocos de _CRT_BLOCK.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49739a0c07426329dc20f7fd459febcc70866ec9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866054"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Ganchos de alocação e alocações de memória de tempo de execução do C
Uma restrição muito importante nas funções de gancho de alocação é que elas devem ignorar `_CRT_BLOCK` blocos explicitamente. Esses blocos são as alocações de memória feitas internamente pelas funções de biblioteca de tempo de execução do C se fizerem chamadas para as funções de biblioteca de tempo de execução C que alocam memória interna. Você pode ignorar `_CRT_BLOCK` blocos incluindo o seguinte código no início da função de seu gancho de alocação:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Se o gancho de alocação não ignorar os `_CRT_BLOCK` blocos, qualquer função de biblioteca de tempo de execução do C chamada em seu gancho poderá interceptar o programa em um loop infinito. Por exemplo, `printf` faz uma alocação interna. Se o código de gancho chamar `printf`, a alocação resultante fará o gancho ser chamado novamente, que chamará **printf** novamente e assim por diante, até o estouro de pilha. Se você precisar reportar operações de alocação `_CRT_BLOCK`, uma maneira de evitar essa restrição é usar funções de API do Windows, em vez de funções de tempo de execução C, para formatação e saída. Como as APIs do Windows não usam o heap de biblioteca de tempo de execução C, elas não interceptarão seu gancho de alocação em um loop infinito.

Se você examinar os arquivos de origem da biblioteca em tempo de execução, verá que a função padrão de gancho de alocação, **CrtDefaultAllocHook** (que retorna apenas **TRUE**), está localizada em um arquivo separado, DBGHOOK.C. Se você quiser que o gancho de alocação seja chamado mesmo para as alocações feitas pelo código de inicialização de tempo de execução que é executado antes da função **principal** de seu aplicativo, você poderá substituir essa função padrão por um de seus próprios, em vez de usar [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Confira também
- [Depurar a gravação da função do gancho](../debugger/debug-hook-function-writing.md)
