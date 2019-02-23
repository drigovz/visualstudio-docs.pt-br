---
title: Campo TASK_STATE_CANCELED | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b022daee6e71cd0728c2c161eb3e75a865304d04
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719711"
---
# <a name="taskstatecanceled-field"></a>Campo TASK_STATE_CANCELED
A tarefa foi cancelada antes que atingiu o estado de execução, ou confirmar seu cancelamento e concluído sem exceção.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em mscorlib. dll)

 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Comentários
 Se o [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contém esse valor, o <xref:System.Threading.Tasks.Task.Status%2A> propriedade retorna <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Consulte também
- [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)