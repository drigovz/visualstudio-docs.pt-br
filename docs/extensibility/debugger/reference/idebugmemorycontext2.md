---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727433"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Esta interface representa uma posição no espaço de endereço da máquina que executa o programa que está sendo depurado.

## <a name="syntax"></a>Sintaxe

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa esta interface para representar um endereço na memória.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) retorna essa interface. Além disso, chamadas para [Adicionar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [Subtrair](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) retornam novas cópias desta interface após a operação aritmética apropriada ter sido aplicada.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugMemoryContext2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtém o nome de exibição do usuário para este contexto.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtém informações que descrevem esse contexto.|
|[Adicionar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Adiciona um valor especificado ao endereço do contexto atual para criar um novo contexto.|
|[Subtrair](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrai um valor especificado do endereço do contexto atual para criar um novo contexto.|
|[Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dois contextos da maneira indicada pelas bandeiras de comparação.|

## <a name="remarks"></a>Comentários
 A janela **Memória** do Visual Studio chama `IDebugMemoryContext2` [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obter a interface que contém a expressão avaliada usada para o endereço de memória. Esse contexto é então passado para [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar o endereço para ler ou gravar.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
