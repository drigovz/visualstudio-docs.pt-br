---
title: 'Como: Definir um nome de Thread em código nativo | Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: acddd39df0c91aeef5c425ffa67cb234d76d0473
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961342"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Como: Definir um nome de thread em código nativo
A nomeação de thread é possível em qualquer edição do Visual Studio. A nomeação de thread é útil para manter o controle de threads na janela **Threads**.

## <a name="set-a-thread-name"></a>Definir um nome de thread

O `SetThreadName` função é útil para definição e exibição de threads se o depurador é anexado ao seu código em execução. A partir do Visual Studio 2017 versão 15.6, você pode usar o [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) função para definir e exibir os nomes de thread.

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

## <a name="set-a-thread-name-using-setthreadname"></a>Definir um nome de thread usando SetThreadName

Para definir um nome de thread em seu programa, você também pode usar o `SetThreadName` de função, conforme mostrado no exemplo de código a seguir. Observe que o nome do thread é copiado para o thread de forma que a memória para o parâmetro `threadName` possa ser liberada.  Esse método usa uma abordagem baseada em exceções que só funciona se o depurador está anexado no momento em que o método baseado em exceção é usado. Um nome de thread que você definir usando esse método não estará disponível em despejos de memória ou ferramentas de análise de desempenho.

O exemplo de código a seguir mostra como usar `SetThreadName`:

```C++
//  
// Usage: SetThreadName ((DWORD)-1, "MainThread");  
//  
#include <windows.h>  
const DWORD MS_VC_EXCEPTION = 0x406D1388;  
#pragma pack(push,8)  
typedef struct tagTHREADNAME_INFO  
{  
    DWORD dwType; // Must be 0x1000.  
    LPCSTR szName; // Pointer to name (in user addr space).  
    DWORD dwThreadID; // Thread ID (-1=caller thread).  
    DWORD dwFlags; // Reserved for future use, must be zero.  
 } THREADNAME_INFO;  
#pragma pack(pop)  
void SetThreadName(DWORD dwThreadID, const char* threadName) {  
    THREADNAME_INFO info;  
    info.dwType = 0x1000;  
    info.szName = threadName;  
    info.dwThreadID = dwThreadID;  
    info.dwFlags = 0;  
#pragma warning(push)  
#pragma warning(disable: 6320 6322)  
    __try{  
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);  
    }  
    __except (EXCEPTION_EXECUTE_HANDLER){  
    }  
#pragma warning(pop)  
}  
```  

## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos multi-threaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Como: Definir o nome de um thread no código gerenciado](../debugger/how-to-set-a-thread-name-in-managed-code.md)