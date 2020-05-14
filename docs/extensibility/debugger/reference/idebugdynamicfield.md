---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731321"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Esta interface representa um tipo de variável.

## <a name="syntax"></a>Sintaxe

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada por provedores de símbolos como uma classe base para qualquer tipo que possa ser determinada em tempo de execução. Isto é apenas para código gerenciado.

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface representa uma classe base da qual interfaces mais especializadas podem ser derivadas.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Esta interface não fornece nenhum método diferente `IDebugField`daqueles herdados .

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
