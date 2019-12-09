---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1abe29a915d8ca2aaba1135d2e57946250bc3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346966"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Essa interface representa uma posição no espaço de endereço do computador que executa o programa que está sendo depurado.

## <a name="syntax"></a>Sintaxe

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface para representar um endereço na memória.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) retorna essa interface. Além disso, chamadas para [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) retornar novas cópias dessa interface depois que a operação aritmética apropriada foi aplicada.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugMemoryContext2`.

|Método|Descrição|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtém o nome de exibição de usuário para este contexto.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtém informações que descrevem neste contexto.|
|[Adicionar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Adiciona um valor especificado para o endereço do contexto atual para criar um novo contexto.|
|[Subtração](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrai um valor especificado do endereço do contexto atual para criar um novo contexto.|
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dois contextos da maneira indicados pelo compara sinalizadores.|

## <a name="remarks"></a>Comentários
 Visual Studio **memória** janela chamadas [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obter o `IDebugMemoryContext2` interface que contém a expressão avaliada usada para o endereço de memória. Nesse contexto é então passado para [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar o endereço para ler ou gravar.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)