---
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e2bcb8f8562b5b20231879d46c64eb73af027f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920252"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Essa interface representa um tipo de enumeração.

## <a name="syntax"></a>Sintaxe

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um provedor de símbolo implementa essa interface para representar uma enumeração.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obter essa interface da [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retorna `FIELD_TYPE_ENUM`.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de VTable
 Além dos métodos na `IDebugField` e `IDebugContainerField` interfaces, essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) descrevendo o nome para esse tipo de enumeração.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Retorna o nome da constante de enumeração associado com o valor fornecido.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Retorna o valor associado com o nome de constante de enumeração fornecida|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Retorna o valor associado com o nome de constante de enumeração fornecida, mas ignora maiusculas/minúsculas.|

## <a name="remarks"></a>Comentários
 É o símbolo subjacente que, na verdade, está associado a um local com [associar](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Requisitos
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Provedor de Símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Associar](../../../extensibility/debugger/reference/idebugbinder-bind.md)