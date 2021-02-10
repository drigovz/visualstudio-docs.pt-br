---
title: Campo de TASK_STATE_FAULTED | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 139893c7bb993180fd35aec1e02559f317ef8156
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968522"
---
# <a name="task_state_faulted-field"></a>Campo de TASK_STATE_FAULTED
A tarefa foi concluída devido a uma exceção sem tratamento.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Comentários
 Se o campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiver esse valor, a <xref:System.Threading.Tasks.Task.Status%2A> propriedade retornará <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Consulte também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
