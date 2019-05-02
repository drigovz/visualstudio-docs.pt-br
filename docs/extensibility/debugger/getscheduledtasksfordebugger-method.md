---
title: Método GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 221a1b49bd3083e0d2dd0248cdf182d699423057
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889925"
---
# <a name="getscheduledtasksfordebugger-method"></a>Método GetScheduledTasksForDebugger
Recupera uma matriz de todas as tarefas agendadas.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em *mscorlib. dll*)

 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valor de retorno
 Uma matriz de todas as tarefas agendadas. Cada tarefa está em execução ou tiver concluído a execução.

## <a name="remarks"></a>Comentários
 Esse método não é thread-safe e não deve ser usada simultaneamente com outras instâncias do <xref:System.Threading.Tasks.TaskScheduler>. Chame esse método de um depurador somente quando o depurador suspendeu a todos os outros threads.

## <a name="see-also"></a>Consulte também
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)