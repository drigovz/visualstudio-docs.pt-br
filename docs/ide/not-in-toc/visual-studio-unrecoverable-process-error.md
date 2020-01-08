---
title: Um processo encontrou um erro irrecuperável
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 206fcddca51f8e770e013ff67de6ae3d5562f633
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585789"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Erro de processo irrecuperável do Visual Studio

O Visual Studio usa vários processos fora do processo para executar tarefas em segundo plano obrigatórias, como o Live Unit Testing, analisadores de código, entre outras. Esses processos são executados fora do processo para fornecer vantagens de desempenho ao Visual Studio, como permitir que ele responda mais rapidamente ao executar trabalhos de longa duração com uso intensivo de recursos. Além disso, como o Visual Studio é um processo de 32 bits, a execução de processos fora do processo fornece ao trabalho com uso intensivo de memória maior espaço de memória no qual operar.

Se o processo *ServiceHub.RoslynCodeAnalysisService.exe* ou *ServiceHub.RoslynCodeAnalysisService32.exe* terminar por algum motivo, uma barra de informações pop-up será exibida com a seguinte mensagem:

**"Infelizmente, um processo usado pelo Visual Studio encontrou um erro irrecuperável. É recomendável salvar seu trabalho e, em seguida, fechar e reiniciar o Visual Studio. "**

Se você receber essa mensagem, salve o trabalho imediatamente e, em seguida, feche e reinicie o Visual Studio.

## <a name="list-of-processes"></a>Lista de processos

A seguir está uma lista de processos fora do processo usados pelo Visual Studio. Essa lista inclui processos que são iniciados em cenários ou fluxos de trabalho específicos e, portanto, geralmente eles não estão todos em execução ao mesmo tempo.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Se um desses processos for encerrado inesperadamente, algumas funcionalidades do Visual Studio deixarão de funcionar. Para alguns processos, a perda de funcionalidade pode ser insignificante. Para outros, a estabilidade do Visual Studio é afetada e uma mensagem de erro é exibida.
