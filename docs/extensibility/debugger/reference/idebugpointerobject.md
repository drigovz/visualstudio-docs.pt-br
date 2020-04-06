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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725497"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface representa um objeto de ponteiro.

## <a name="syntax"></a>Sintaxe

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa esta interface para representar um objeto de ponteiro.

## <a name="notes-for-callers"></a>Observações para chamadores
 A interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) pode obter essa interface `IDebugObject` usando [o QueryInterface](/cpp/atl/queryinterface) se o ponteiro representar um ponteiro.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos herdados do [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md)a `IDebugPointerObject` interface expõe os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[Desreferenciar](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Obtém o objeto para o qual a interface aponta.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Obtém o valor para o qual a interface aponta como uma série de bytes consecutivos.|
|[Setbytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Define o valor para o qual a interface aponta a partir de uma série de bytes consecutivos.|

## <a name="remarks"></a>Comentários
 Um avaliador de expressão usa essa interface para representar um ponteiro em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
