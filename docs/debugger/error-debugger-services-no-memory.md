---
title: Os serviços do depurador estão ficando sem memória | Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737835"
---
# <a name="debugger-services-running-out-of-memory"></a>Memória insuficiente para os serviços do depurador
Os serviços de depuração esgotaram a memória e causaram o encerramento da sessão de depuração.

## <a name="to-investigate-this-error-on-windows"></a>Para investigar esse erro no Windows
- Você pode verificar o grafo memória do processo na janela **ferramentas de diagnóstico** para ver se o aplicativo de destino está apresentando um enorme crescimento na memória. Nesse caso, use a ferramenta de **uso de memória** para diagnosticar qual é o problema subjacente, consulte analisar o [uso de memória](../profiling/memory-usage.md).

- Se o aplicativo de destino não estiver consumindo muita memória, use a janela do **Gerenciador de tarefas** para verificar o uso de memória do Visual Studio (devenv. exe), o processo de trabalho (msvsmon. exe) ou de vs Code (vsdbg. exe/vsdbg-UI. exe) para determinar se este é um problema do depurador. Se o processo que está ficando sem memória for devenv. exe, considere a possibilidade de reduzir o número de extensões do Visual Studio em execução.

## <a name="see-also"></a>Consulte também
- [Postagem no blog: analisar a CPU e a memória durante a depuração](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Sobre o gerenciamento de memória](/windows/win32/memory/about-memory-management)
