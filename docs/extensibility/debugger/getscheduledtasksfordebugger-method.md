---
title: Obtertarefas programadasParao método dedepuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738654"
---
# <a name="getscheduledtasksfordebugger-method"></a>Método GetScheduledTasksForDebugger
Recupera uma matriz de todas as tarefas programadas.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

 Como você não pode acessar este membro interno do .NET Framework, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valor retornado
 Uma série de tarefas programadas. Cada tarefa está executando ou terminou de executar.

## <a name="remarks"></a>Comentários
 Este método não é seguro para rosca e você não <xref:System.Threading.Tasks.TaskScheduler>deve usá-lo simultaneamente com outras instâncias de . Chame este método de um depurador somente quando o depurador tiver suspendido todos os outros segmentos.

## <a name="see-also"></a>Confira também
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
