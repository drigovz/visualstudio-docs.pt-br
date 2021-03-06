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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cce45c926700779906881bc4a4607b05f0732be3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956393"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Essa interface representa uma coleção de objetos que implementam a interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Sintaxe

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada pelo provedor de símbolos para fornecer conjuntos de objetos que implementam a interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Observe que essa não é uma enumeração COM padrão devido à presença do método [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é retornada por [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) e [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Essa interface implementa os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[Próximo](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera o próximo conjunto de objetos [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) da enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Ignora um número especificado de entradas.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Redefine a enumeração para a primeira entrada.|
|[8i](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera uma cópia da enumeração atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera o número de entradas na enumeração.|

## <a name="remarks"></a>Comentários

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
