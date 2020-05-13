---
title: AsyncTaskMethodBuilder&lt;Tresult&gt; Structure - Membros internos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c4f4da7070af09937af9e047ec83142584942e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739339"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; - membros internos
Este tópico descreve os membros <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> internos da classe. Para obter informações gerais sobre <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> esta classe, consulte o tópico de referência.

 **Espaço de nome:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Montagem:** mscorlib (in mscorlib.dll)

 Como você não pode acessar esses membros internos do Quadro .NET, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membros internos

|Nome|Descrição|
|----------|-----------------|
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar exclusivamente este construtor para o depurador.|
|[campo m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Representa a tarefa preguiçosamente inicializada construída.|

## <a name="see-also"></a>Confira também
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Internos de extensão paralelas para o Quadro .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
