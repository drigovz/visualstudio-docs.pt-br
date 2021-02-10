---
title: Campo de TASK_STATE_RAN_TO_COMPLETION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f8eedfba005848dbb44d194a6210966ec0fda736
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968535"
---
# <a name="task_state_ran_to_completion-field"></a>Campo de TASK_STATE_RAN_TO_COMPLETION
A execução da tarefa foi concluída com êxito.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)
```

## <a name="remarks"></a>Comentários
 Se o campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiver esse valor, a <xref:System.Threading.Tasks.Task.Status%2A> propriedade retornará <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Consulte também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
