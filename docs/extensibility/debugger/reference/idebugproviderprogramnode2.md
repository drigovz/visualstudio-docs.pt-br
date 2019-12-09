---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33c4a4914e15a8ecbea0d4f28c2325a952a042de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353812"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Essa interface realiza marshaling de interfaces relacionadas ao programa nos limites do processo.

## <a name="syntax"></a>Sintaxe

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface no mesmo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para dar suporte a interfaces de marshaling entre limites de processo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [QueryInterface](/cpp/atl/queryinterface) em um `IDebugProgramNode2` interface para obter essa interface. Se essa interface não pode ser obtida, o DE não suporta o marshaling de interfaces.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Essa interface implementa o método a seguir:

|Método|Descrição|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtém uma interface especificada nos limites do processo.|

## <a name="remarks"></a>Comentários
 Essa interface é implementada quando a Alemanha é executado em um espaço de processo separado do programa que está sendo depurado: por exemplo, quando o DE está em execução no espaço de processo do Visual Studio em vez de espaço de processo do programa que está sendo depurado.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)