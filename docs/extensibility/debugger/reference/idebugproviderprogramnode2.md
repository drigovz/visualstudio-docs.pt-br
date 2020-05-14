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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720687"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Essa interface empacota interfaces relacionadas ao programa através dos limites do processo.

## <a name="syntax"></a>Sintaxe

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface no mesmo objeto que implementa o [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para suportar interfaces de marshaling entre os limites do processo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para o `IDebugProgramNode2` [QueryInterface](/cpp/atl/queryinterface) em uma interface para obter essa interface. Se esta interface não puder ser obtida, o DE não suportará o empacotamento de interfaces.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtém uma interface especificada entre os limites do processo.|

## <a name="remarks"></a>Comentários
 Essa interface é implementada quando o DE é executado em um espaço de processo separado do programa que está sendo depurado: por exemplo, quando o DE está sendo executado no espaço de processo do Visual Studio em vez do espaço de processo do programa ser depurado.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
