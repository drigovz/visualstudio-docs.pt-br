---
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c884f2794031d92add956bf4364824165ee1edfb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343922"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface representa um objeto de ponteiro.

## <a name="syntax"></a>Sintaxe

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O avaliador de expressão implementa essa interface para representar um objeto de ponteiro.

## <a name="notes-for-callers"></a>Observações para chamadores
 O [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pode obter essa interface usando [QueryInterface](/cpp/atl/queryinterface) se o `IDebugObject` representa um ponteiro.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos herdados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), o `IDebugPointerObject` interface expõe os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[Desreferenciar](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtém o objeto para o qual a interface aponta.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtém o valor para o qual a interface aponta como uma série de bytes consecutivos.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Define o valor para o qual a interface aponta de uma série de bytes consecutivos.|

## <a name="remarks"></a>Comentários
 Um avaliador de expressão usa essa interface para representar um ponteiro em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Avaliação de Expressões](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)