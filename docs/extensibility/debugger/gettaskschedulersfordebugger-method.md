---
title: ObterTaskSchedulersForDebugger Method | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738653"
---
# <a name="gettaskschedulersfordebugger-method"></a>Método GetTaskSchedulersForDebugger
Recupera uma matriz <xref:System.Threading.Tasks.TaskScheduler> de todos os objetos que estão ativos no momento.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

 Como você não pode acessar este membro interno do .NET Framework, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valor retornado
 Uma matriz <xref:System.Threading.Tasks.TaskScheduler> de todos os objetos <xref:System.AppDomain>que estão atualmente ativos neste .

## <a name="remarks"></a>Comentários
 Este método não é seguro para rosca e você não <xref:System.Threading.Tasks.TaskScheduler>deve usá-lo simultaneamente com outras instâncias de . Chame este método de um depurador somente quando o depurador tiver suspendido todos os outros segmentos.

## <a name="see-also"></a>Confira também
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
