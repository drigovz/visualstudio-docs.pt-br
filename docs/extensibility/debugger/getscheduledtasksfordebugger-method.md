---
title: Método GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49a63462eece9bef09579c7284f72790a3914bc2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353727"
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