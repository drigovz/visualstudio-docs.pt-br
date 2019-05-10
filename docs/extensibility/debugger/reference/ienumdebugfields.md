---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cdb01a98a2cb2b2038366f0968c3b3532bd9ffc
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225594"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Essa interface representa uma coleção de objetos que implementam o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada pelo provedor de símbolo para fornecer conjuntos de objetos que implementam o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface. Observe que isso não é uma enumeração COM padrão devido à presença do [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) método.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é retornada por [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) e [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Essa interface implementa os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera o próximo conjunto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos da enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Ignora um número especificado de entradas.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Redefine a enumeração para a primeira entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera uma cópia da enumeração atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera o número de entradas na enumeração.|

## <a name="remarks"></a>Comentários

## <a name="requirements"></a>Requisitos
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Provedor de Símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)