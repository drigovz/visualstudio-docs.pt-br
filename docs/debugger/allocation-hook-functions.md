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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f90e6db9a86457d0a9a0c7c4f61edac5d997414
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823909"
---
# <a name="allocation-hook-functions"></a>Funções de gancho da alocação
Uma função de gancho de alocação, instalada usando [crtsetallochook](/cpp/c-runtime-library/reference/crtsetallochook), é chamado sempre que a memória é alocada, realocada ou liberada. Você pode usar esse tipo de gancho para muitas finalidades diferentes. Usá-lo para testar como um aplicativo trata situações de memória insuficiente, por exemplo, para examinar padrões de alocação ou registrar informações de alocação para análise posterior.  
  
> [!NOTE]
>  Lembre-se da restrição sobre as funções da biblioteca em tempo de execução C em uma função de gancho de alocação, descrita em [Ganchos de alocação e alocações de memória de tempo de execução C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
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
  
 Quando a biblioteca de tempo de execução chama seu gancho, o *nAllocType* argumento indica quais alocação operação está prestes a ser realizada (**hook_alloc**, **hook_realloc**, ou **Hook_free**). Em um livre ou em uma realocação, `pvData` tem um ponteiro para o artigo de usuário do bloco para ser liberado. No entanto para uma alocação, esse ponteiro é null, porque a alocação ainda não ocorreu. Os argumentos restantes contêm o tamanho da alocação em questão, seu tipo de bloco, o número sequencial da solicitação associada com ele e um ponteiro para o nome do arquivo. Se estiver disponível, os argumentos também incluem o número da linha na qual a alocação foi feita. Depois que a função de gancho executar as análises e outras tarefas que o autor desejar, ela deverá retornar **TRUE**, indicando que a operação de alocação pode continuar ou **FALSE**, indicando que a operação falhará. Um gancho simples desse tipo poderá verificar a quantidade de memória alocada até o momento e retornar **FALSE** se essa quantidade exceder um limite pequeno. O aplicativo apresentaria o tipo de erros de alocação que ocorreriam normalmente apenas quando a memória disponível estivesse muito baixa. Ganchos mais complexos podem controlar os padrões de alocação, analisar o uso de memória ou reportar quando as situações específicas surgem.  
  
## <a name="see-also"></a>Consulte também  
 [Ganchos de alocação e alocações de memória do tempo de execução do C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)   
