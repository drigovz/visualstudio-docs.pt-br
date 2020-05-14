---
title: IDebugArrayField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736296"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Esta interface descreve um símbolo ou tipo de matriz.

## <a name="syntax"></a>Sintaxe

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O provedor de símbolos implementa essa interface no mesmo objeto que implementa a interface [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Esta interface é uma especialização que representa objetos de matriz.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [queryInterface](/cpp/atl/queryinterface) para obter esta interface a partir da interface `FIELD_TYPE_ARRAY` [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) se [getKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retornar o sinalizador .

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos nas interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) esta interface implementa o seguinte:

|Método|Descrição|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Obtém o número de elementos na matriz.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Obtém o tipo de elemento na matriz.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Obtém a classificação da matriz.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
