---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720687"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Essa interface empacota interfaces relacionadas a programas entre limites de processo.

## <a name="syntax"></a>Syntax

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface no mesmo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para dar suporte a interfaces de marshaling entre limites de processo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [QueryInterface](/cpp/atl/queryinterface) em uma `IDebugProgramNode2` interface para obter essa interface. Se essa interface não puder ser obtida, a DE não oferecerá suporte ao marshaling de interfaces.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Essa interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtém uma interface especificada entre limites de processo.|

## <a name="remarks"></a>Comentários
 Essa interface é implementada quando a DE é executada em um espaço de processo separado do programa que está sendo depurado: por exemplo, quando o DE está em execução no espaço de processo do Visual Studio, em vez do espaço de processo do programa que está sendo depurado.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
