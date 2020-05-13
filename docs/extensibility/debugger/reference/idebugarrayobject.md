---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736219"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface representa um objeto de matriz.

## <a name="syntax"></a>Sintaxe

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa essa interface para representar uma matriz.

## <a name="notes-for-callers"></a>Observações para chamadores
 A interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) pode obter essa interface usando [o QueryInterface](/cpp/atl/queryinterface) se o objeto representar uma matriz.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos na `IDebugObject` interface, os seguintes métodos são implementados na `IDebugArrayObject` interface.

|Método|Descrição|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtém a contagem de elementos na matriz.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtém um elemento da matriz.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtém todos os elementos da matriz.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtém a classificação da matriz.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtém as dimensões da matriz.|

## <a name="remarks"></a>Comentários
 Um avaliador de expressão usa essa interface para representar matrizes em uma árvore de análise.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
