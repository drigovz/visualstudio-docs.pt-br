---
title: Estrutura de construtor asyncVoidMethod - Membros internos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739291"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Estrutura AsyncVoidMethodBuilder - membros internos
Este tópico descreve os membros <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> internos da classe. Para obter informações gerais sobre <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> esta classe, consulte o tópico de referência.

 **Espaço de nome:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Montagem:** mscorlib (in mscorlib.dll)

 Como você não pode acessar esses membros internos do Quadro .NET, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membros internos

|Nome|Descrição|
|----------|-----------------|
|[Propriedade ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtém um objeto que pode ser usado para identificar exclusivamente este construtor para o depurador.|
|[m_objectIdForDebugger campo](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Representa o objeto preguiçosamente inicializado usado pelo depurador para identificar exclusivamente este construtor.|

## <a name="see-also"></a>Confira também
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Internos de extensão paralelas para o Quadro .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
