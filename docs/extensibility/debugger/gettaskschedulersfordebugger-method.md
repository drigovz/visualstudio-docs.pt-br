---
title: Método GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738653"
---
# <a name="gettaskschedulersfordebugger-method"></a>Método GetTaskSchedulersForDebugger
Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

 Como você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valor retornado
 Uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão atualmente ativos neste <xref:System.AppDomain> .

## <a name="remarks"></a>Comentários
 Esse método não é thread-safe e você não deve usá-lo simultaneamente com outras instâncias do <xref:System.Threading.Tasks.TaskScheduler> . Chame esse método de um depurador somente quando o depurador tiver suspenso todos os outros threads.

## <a name="see-also"></a>Confira também
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
