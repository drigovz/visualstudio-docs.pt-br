---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d94a685b9c79069a047e32155234f9bf6a50d5c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875395"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Essa interface representa um tipo de uma variável.

## <a name="syntax"></a>Sintaxe

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada por provedores de símbolo como uma classe base para qualquer tipo que pode ser determinada em tempo de execução. Isso é apenas para código gerenciado.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface representa uma classe base da qual as interfaces mais especializadas podem ser derivadas.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Essa interface fornece métodos que não sejam aqueles herdados de `IDebugField`.

## <a name="requirements"></a>Requisitos
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Provedor de Símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)