---
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725497"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface representa um objeto de ponteiro.

## <a name="syntax"></a>Syntax

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa essa interface para representar um objeto de ponteiro.

## <a name="notes-for-callers"></a>Observações para chamadores
 A interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) pode obter essa interface usando [QueryInterface](/cpp/atl/queryinterface) se o `IDebugObject` representar um ponteiro.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Além dos métodos herdados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), a `IDebugPointerObject` interface expõe os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[Desreferenciar](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtém o objeto ao qual a interface aponta.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtém o valor para o qual a interface aponta como uma série de bytes consecutivos.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Define o valor para o qual a interface aponta de uma série de bytes consecutivos.|

## <a name="remarks"></a>Comentários
 Um avaliador de expressão usa essa interface para representar um ponteiro em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
