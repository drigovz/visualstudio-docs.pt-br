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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725601"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Essa interface representa um tipo de ponteiro.

## <a name="syntax"></a>Syntax

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O provedor de símbolos implementa essa interface para representar um ponteiro.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obter essa interface da interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) se [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retornar `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Além dos métodos nas `IDebugField` `IDebugContainerField` interfaces e, essa interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que descreve o destino do ponteiro.|

## <a name="remarks"></a>Comentários
 Em C/C++, um ponteiro pode ser um contêiner se for usado com notação de matriz. Por exemplo, fornecido `char *pString` , `pString` tem um tipo de ponteiro para `char` . `pString[3]` tem o tipo de um contêiner que é um ponteiro para `char` o qual faz referência ao quarto elemento desse contêiner.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
