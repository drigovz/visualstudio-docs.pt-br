---
title: Campo de TASK_STATE_WAITING_ON_CHILDREN | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2dfb7ca683b7a05151539feda92a2575197b189
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176709"
---
# <a name="task_state_waiting_on_children-field"></a>Campo TASK_STATE_WAITING_ON_CHILDREN
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A tarefa concluiu a execução de seu delegado e está esperando implicitamente que as tarefas filho anexadas sejam concluídas.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (no mscorlib.dll)  
  
 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## <a name="remarks"></a>Comentários  
 Se o campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiver esse valor, a <xref:System.Threading.Tasks.Task.Status%2A> propriedade retornará <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Consulte Também  
 [Classe de tarefa](../../extensibility/debugger/task-class-internal-members.md)
