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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731321"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Essa interface representa um tipo de variável.

## <a name="syntax"></a>Syntax

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada por provedores de símbolos como uma classe base para qualquer tipo que possa ser determinado em tempo de execução. Isso é apenas para código gerenciado.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface representa uma classe base da qual interfaces mais especializadas podem ser derivadas.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Esta interface não fornece nenhum método diferente daqueles herdados de `IDebugField` .

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
