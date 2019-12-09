---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9101f1c2faeedf8b08b3b11044eaa22f6c6d512a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352872"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Essa interface representa as informações necessárias para criar e associar a qualquer tipo de ponto de interrupção. Ele é uma extensão da [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Sintaxe

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O Gerenciador de sessão de depuração (SDM) normalmente implementa essa interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 O mecanismo de depuração (DES) acessa essa interface chamando [QueryInterface](/cpp/atl/queryinterface) na interface IDebugBreakpointRequest2 recebido em uma chamada para [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos herdados de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), o `IDebugBreakpointRequest3` interface expõe o método a seguir.

|Método|Descrição|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtém as informações de solicitação de ponto de interrupção que descreve esta solicitação de ponto de interrupção.|

## <a name="remarks"></a>Comentários
 Essa interface é usada para fornecer informações adicionais para o DE por meio de [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura. Essas informações adicionais incluem a ID do fornecedor da Alemanha (na forma de um GUID), o nome de um tracepoint e o nome de uma restrição de ponto de interrupção.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)