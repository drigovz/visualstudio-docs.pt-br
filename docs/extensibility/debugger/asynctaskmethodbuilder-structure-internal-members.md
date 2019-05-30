---
title: Estrutura AsyncTaskMethodBuilder - membros internos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f080e7a0fef7a03b878c253f09661338b5704df
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317641"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Estrutura AsyncTaskMethodBuilder - membros internos
Este tópico descreve os membros internos do <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe. Para obter informações gerais sobre essa classe, consulte o <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> tópico de referência.

 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (em mscorlib. dll)

 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membros internos

|Nome|Descrição|
|----------|-----------------|
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar exclusivamente esse construtor para o depurador.|
|[campo m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa o objeto de construtor genérico ao qual esta instância não genérica delega.|

## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)