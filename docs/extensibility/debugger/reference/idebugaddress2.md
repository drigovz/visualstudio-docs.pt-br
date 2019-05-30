---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66fd149bc3eed7633586c156f6493c8febcbeaac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330355"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Essa interface fornece acesso para a ID do processo que possui o objeto cujo endereço é representado por esta interface.

## <a name="syntax"></a>Sintaxe

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Essa interface fornece acesso para a identificação do processo que possui o objeto que está relacionado a esse endereço.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obter essa interface da [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

## <a name="methods-in-vtable-order"></a>Métodos em vtable ordem
 Além dos métodos herdados do [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface, essa interface implementa o método a seguir:

|Método|Descrição|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera a ID do processo que possui o objeto representado por esta interface.|

## <a name="requirements"></a>Requisitos
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Provedor de Símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)