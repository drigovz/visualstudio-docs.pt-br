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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716258"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface representa uma coleção de objetos que implementam a interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="syntax"></a>Syntax

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
|[Próximo](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera o próximo conjunto de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) da enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignora um número especificado de entradas.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Redefine a enumeração para a primeira entrada.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera uma cópia da enumeração atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera o número de entradas na enumeração.|

## <a name="remarks"></a>Comentários
 Essa interface permite que um mecanismo de depuração enumere um conjunto de objetos em uma matriz.

## <a name="requirements"></a>Requisitos
 Cabeçalho: EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
