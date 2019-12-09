---
title: Funções de gancho de alocação | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f684c6c66448fdab2ee7607a81ff7ed769a5e607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745817"
---
# <a name="allocation-hook-functions"></a>Funções de gancho da alocação
Uma função de gancho de alocação, instalada usando [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), é chamada toda vez que a memória é alocada, realocada ou liberada. Você pode usar esse tipo de gancho para várias finalidades diferentes. Use-o para testar como um aplicativo lida com situações de memória insuficientes, como para examinar padrões de alocação ou informações de alocação de log para análise posterior.

> [!NOTE]
> Lembre-se da restrição sobre as funções da biblioteca em tempo de execução C em uma função de gancho de alocação, descrita em [Ganchos de alocação e alocações de memória de tempo de execução C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Uma função de gancho de alocação deve ter um protótipo como o exemplo a seguir:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 O ponteiro que você passa para [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) é do tipo **_CRT_ALLOC_HOOK**, conforme definido em CRTDBG.H:

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Quando a biblioteca de tempo de execução chama seu gancho, o argumento *nAllocType* indica qual operação de alocação está prestes a ser feita ( **_HOOK_ALLOC**, **_HOOK_REALLOC**ou **_HOOK_FREE**). Em uma realocação gratuita ou em uma realocação, `pvData` tem um ponteiro para o artigo do usuário do bloco a ser liberado. No entanto, para uma alocação, esse ponteiro é nulo porque a alocação não ocorreu. Os argumentos restantes contêm o tamanho da alocação em questão, seu tipo de bloco, o número de solicitação sequencial associado a ele e um ponteiro para o nome do arquivo. Se disponível, os argumentos também incluem o número de linha no qual a alocação foi feita. Depois que a função de gancho executar as análises e outras tarefas que o autor desejar, ela deverá retornar **TRUE**, indicando que a operação de alocação pode continuar ou **FALSE**, indicando que a operação falhará. Um gancho simples desse tipo poderá verificar a quantidade de memória alocada até o momento e retornar **FALSE** se essa quantidade exceder um limite pequeno. O aplicativo apresentaria o tipo de erros de alocação que ocorreriam normalmente apenas quando a memória disponível estivesse muito baixa. Ganchos mais complexos podem controlar os padrões de alocação, analisar o uso de memória ou reportar quando as situações específicas surgem.

## <a name="see-also"></a>Consulte também

- [Ganchos de alocação e alocações de memória de tempo de execução do C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)