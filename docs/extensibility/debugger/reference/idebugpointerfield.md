---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725601"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Esta interface representa um tipo de ponteiro.

## <a name="syntax"></a>Sintaxe

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O provedor de símbolos implementa essa interface para representar um ponteiro.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [queryInterface](/cpp/atl/queryinterface) para obter esta interface a partir da `FIELD_TYPE_POINTER`interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) se [getKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retornar .

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Além dos métodos e `IDebugField` `IDebugContainerField` interfaces, esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) descrevendo o alvo do ponteiro.|

## <a name="remarks"></a>Comentários
 Em C/C++, um ponteiro pode ser um recipiente se for usado com notação de matriz. Por exemplo, `char *pString` `pString` dado, tem `char`um tipo de ponteiro para . `pString[3]`tem o tipo de recipiente que `char` é um ponteiro para que faz referência ao quarto elemento desse recipiente.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
