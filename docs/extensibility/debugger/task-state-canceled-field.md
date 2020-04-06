---
title: campo TASK_STATE_CANCELED | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712757"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED campo
A tarefa foi cancelada antes de chegar ao estado em execução, ou confirmou seu cancelamento e foi concluída sem exceção.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in mscorlib.dll)

 Como você não pode acessar este membro interno do .NET Framework, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Comentários
 Se o campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiver esse valor, a <xref:System.Threading.Tasks.Task.Status%2A> propriedade reaverá <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Confira também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
