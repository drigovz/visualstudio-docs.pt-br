---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 749b3faf938fbc862fdf9b406127c898ee6b6d98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727569"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface representa uma coleção de objetos que implementam a interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="syntax"></a>Sintaxe

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa essa interface para fornecer conjuntos de objetos que implementam a interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) . Observe que essa não é uma enumeração COM padrão devido à presença do método [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) .

## <a name="notes-for-callers"></a>Observações para chamadores
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) retorna essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Essa interface implementa os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera o próximo conjunto de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) da enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignora um número especificado de entradas.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Redefine a enumeração para a primeira entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera uma cópia da enumeração atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera o número de entradas na enumeração.|

## <a name="remarks"></a>Comentários
 Essa interface permite que um mecanismo de depuração enumere um conjunto de objetos em uma matriz.

## <a name="requirements"></a>Requisitos
 Cabeçalho: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft. VisualStudio. Debugger. Interop. dll

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)