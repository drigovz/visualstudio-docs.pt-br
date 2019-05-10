---
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 261c40fcabf9d5fe3fa99e89a43734bb8f9f245c
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223328"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Essa interface representa uma coleção de objetos que implementam o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada pelo provedor de símbolo para fornecer conjuntos de objetos que implementam o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Observe que isso não é uma enumeração COM padrão devido à presença do [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) método.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é retornada por [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Essa interface implementa os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera o próximo conjunto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objetos da enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignora um número especificado de entradas.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Redefine a enumeração para a primeira entrada.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera uma cópia da enumeração atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera o número de entradas na enumeração.|

## <a name="remarks"></a>Comentários
 Normalmente, essa interface é usada pelo mecanismo de depuração para ajudar a determinar o endereço apropriado para dar ao avaliador de expressão.

## <a name="requirements"></a>Requisitos
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Provedor de Símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)