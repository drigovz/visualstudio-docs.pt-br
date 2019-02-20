---
title: 'Como: definir um nome de Thread em código nativo | Microsoft Docs'
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c547dd00f7a5a31b949d22c13f305050355207c7
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227310"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Como definir um nome de thread em código nativo
A nomeação de thread é possível em qualquer edição do Visual Studio. Nomeação de thread é útil para identificar threads de seu interesse na **Threads** janela ao depurar um processo em execução. Ter chamado recognizably threads também pode ser útil ao executar por meio de inspeção de despejo de pane e analisar o desempenho da captura usando várias ferramentas de depuração de post-mortem.

## <a name="ways-to-set-a-thread-name"></a>Maneiras de definir um nome de thread

Há duas maneiras de definir um nome de thread. A primeira é por meio de [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) função. A segunda é lançando uma exceção específica, enquanto o depurador do Visual Studio é anexado ao processo. Cada abordagem tem vantagens e limitações.

Vale a pena observar que _ambos_ abordagens podem ser usadas em conjunto, se desejado, uma vez que os mecanismos pelos quais eles funcionam são independentes uns dos outros.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Definir um nome de thread usando `SetThreadDescription`

Benefícios:
* Nomes de thread são visíveis durante a depuração no Visual Studio, independentemente de estarem ou não o depurador foi anexado ao processo no momento em que SetThreadDescription é invocado.
* Nomes de thread são visíveis ao realizar a depuração de post-mortem carregando um despejo de memória no Visual Studio.
* Nomes de thread também são visíveis quando usar outras ferramentas, como o [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) depurador e o [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) analisador de desempenho.

Restrições:
* Nomes de thread somente são visíveis no Visual Studio 2017 versão 15.6 e posterior.
* Quando o arquivo de despejo de depuração de uma falha de post-mortem, nomes de thread são visíveis apenas se a falha foi criada no Windows 10 versão 1607, Windows Server 2016 ou versões posteriores do Windows.

*Exemplo:*

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Definir um nome de thread lançando uma exceção

Outra maneira de definir um nome de thread em seu programa é comunicar-se o nome do thread desejado para o depurador do Visual Studio, lançando uma exceção especialmente configurado.

Benefícios:
* Funciona em todas as versões do Visual Studio.

Restrições:
* Só funcionará se o depurador está anexado no momento em que o método baseado em exceção é usado.
* Nomes de thread definidos usando esse método não estará disponíveis em despejos de memória ou ferramentas de análise de desempenho.

*Exemplo:*

O `SetThreadName` função mostrada a seguir demonstra essa abordagem baseada em exceções. Observe que o nome do thread será copiado automaticamente para o thread, para que a memória para o `threadName` parâmetro pode ser liberado após a `SetThreadName` chamada ser concluída.

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
[Como definir um nome de thread em código gerenciado](../debugger/how-to-set-a-thread-name-in-managed-code.md)
