---
title: Método GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5df6dc3147a92f14d6858a82a6d997442dec30b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925648"
---
# <a name="gettaskschedulersfordebugger-method"></a>Método GetTaskSchedulersForDebugger
Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em *mscorlib. dll*)

 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valor retornado
 Uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento desta <xref:System.AppDomain>.

## <a name="remarks"></a>Comentários
 Esse método não é thread-safe e não deve ser usada simultaneamente com outras instâncias do <xref:System.Threading.Tasks.TaskScheduler>. Chame esse método de um depurador somente quando o depurador suspendeu a todos os outros threads.

## <a name="see-also"></a>Consulte também
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)