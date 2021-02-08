---
title: Campo de TASK_STATE_WAITING_ON_CHILDREN | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 052b1dd454ca091b0d83becbd02909c7cd92d00e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837457"
---
# <a name="task_state_waiting_on_children-field"></a>Campo de TASK_STATE_WAITING_ON_CHILDREN
A tarefa concluiu a execução de seu delegado e está esperando implicitamente que as tarefas filho anexadas sejam concluídas.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Comentários
 Se o campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiver esse valor, a <xref:System.Threading.Tasks.Task.Status%2A> propriedade retornará <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
