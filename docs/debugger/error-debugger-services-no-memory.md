---
title: Serviços em execução fora da memória do depurador | Microsoft Docs
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
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854013"
---
# <a name="debugger-services-running-out-of-memory"></a>Serviços em execução fora da memória do depurador
Os serviços de depuração ficou sem memória e causou o encerramento da sessão de depuração.

## <a name="to-investigate-this-error-on-windows"></a>Para examinar esse erro no Windows
- Você pode verificar o gráfico de memória de processo na **das ferramentas de diagnóstico** janela para ver se o aplicativo de destino está experimentando o enorme crescimento de memória. Nesse caso, use o **uso de memória** ferramenta para diagnosticar o que é o problema subjacente, consulte [analisar o uso de memória](../profiling/memory-usage.md).

- Se o aplicativo de destino não parece estar consumindo muita memória, use o **Gerenciador de tarefas** janela para verificar o uso de memória do Visual Studio (devenv.exe), o processo de trabalho (msvsmon.exe) ou do VS Code (vsdbg.exe/vsdbg-ui.exe) para Determine se este é um problema de depurador. Se o processo em execução sem memória for devenv.exe, considere a redução do número de extensões do Visual Studio em execução.

## <a name="see-also"></a>Consulte também
- [Postagem no blog: Analisar a CPU e memória durante a depuração](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Sobre o gerenciamento de memória](/windows/win32/memory/about-memory-management)
