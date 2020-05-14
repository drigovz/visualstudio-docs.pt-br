---
title: Classe TaskScheduler - Membros Internos | Microsoft Docs
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
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712572"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - Membros internos
Este artigo descreve os membros <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> internos da classe que ajudam você a implementar um depurador personalizado. Para obter informações gerais sobre <xref:System.Threading.Tasks.TaskScheduler> esta classe, consulte o artigo de referência.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in *mscorlib.dll*)

 Como você não pode acessar esses membros internos do Quadro .NET, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|Nome|Descrição|
|----------|-----------------|
|[Obtertarefas agendadasParadepurador](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera uma matriz de todas as tarefas programadas.|
|[ObtenhataskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera uma matriz <xref:System.Threading.Tasks.TaskScheduler> de todos os objetos que estão ativos no momento.|

## <a name="remarks"></a>Comentários

## <a name="see-also"></a>Confira também
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Internos de extensão paralelas para o Quadro .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
