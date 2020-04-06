---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716258"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface representa uma coleção de objetos que implementam a interface [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="syntax"></a>Sintaxe

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O avaliador de expressão implementa essa interface para fornecer conjuntos de objetos que implementam a interface [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md) Observe que esta não é uma enumeração COM padrão devido à presença do método [GetCount.](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)

## <a name="notes-for-callers"></a>Observações para chamadores
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) retorna esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Esta interface implementa os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera o próximo conjunto de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) da enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Salta um número especificado de entradas.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Redefine a enumeração para a primeira entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera uma cópia da enumeração atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera o número de entradas na enumeração.|

## <a name="remarks"></a>Comentários
 Esta interface permite que um mecanismo de depuração enumerar sobre um conjunto de objetos em uma matriz.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
