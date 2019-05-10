---
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3c93bde1395a1eec960085c640463e70dee3397
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225845"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Enumera os atributos personalizados.

## <a name="syntax"></a>Sintaxe

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um provedor de símbolo implementa essa interface para dar suporte a atributos personalizados (por meio de [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) interface).

## <a name="notes-for-callers"></a>Observações para chamadores
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) retorna essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IEnumDebugCustomAttributes`.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Recupera um número especificado de atributos personalizados em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Ignora um número especificado de atributos personalizados em uma sequência de enumeração.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Obtém o número de atributos personalizados em um enumerador.|

## <a name="requirements"></a>Requisitos
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Provedor de Símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)