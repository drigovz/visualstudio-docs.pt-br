---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d577ff2f5848f2cb348bcaccf57875507018634b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716784"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Esta interface representa uma coleção de objetos que implementam a interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Sintaxe

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada pelo provedor de símbolos para fornecer conjuntos de objetos que implementam a interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Observe que esta não é uma enumeração COM padrão devido à presença do método [GetCount.](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é retornada por [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) e [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Esta interface implementa os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera o próximo conjunto de objetos [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) da enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Salta um número especificado de entradas.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Redefine a enumeração para a primeira entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera uma cópia da enumeração atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera o número de entradas na enumeração.|

## <a name="remarks"></a>Comentários

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
