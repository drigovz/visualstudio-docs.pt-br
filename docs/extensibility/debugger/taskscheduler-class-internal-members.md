---
title: Classe TaskScheduler – membros internos | Microsoft Docs
description: Saiba mais sobre os membros internos da classe System. Threading. Tasks. TaskScheduler que ajudam a implementar um depurador personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10528e57137f8605e7f140d4ab8d4a3399029a5f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996000"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler – membros internos
Este artigo descreve os membros internos da <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe que ajudam a implementar um depurador personalizado. Para obter informações gerais sobre essa classe, consulte o <xref:System.Threading.Tasks.TaskScheduler> artigo de referência.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (no *mscorlib.dll*)

 Como você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|Nome|Descrição|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera uma matriz de todas as tarefas agendadas.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera uma matriz de todos os <xref:System.Threading.Tasks.TaskScheduler> objetos que estão ativos no momento.|

## <a name="remarks"></a>Comentários

## <a name="see-also"></a>Confira também
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Elementos internos de extensão paralela para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
