---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734822"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Esta interface representa as informações necessárias para criar e vincular qualquer tipo de ponto de ruptura. É uma extensão do [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Sintaxe

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O SDM (Session Debug Manager, gerenciador de depuração de sessão) normalmente implementa essa interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 O mecanismo de depuração (DE) acessa esta interface chamando [QueryInterface](/cpp/atl/queryinterface) na interface IDebugBreakpointRequest2 recebida em uma chamada para [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos herdados do [IDebugBreakpointRequest2,](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)a `IDebugBreakpointRequest3` interface expõe o seguinte método.

|Método|Descrição|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtém as informações de solicitação de ponto de ruptura que descrevem essa solicitação de ponto de ruptura.|

## <a name="remarks"></a>Comentários
 Esta interface é usada para fornecer informações adicionais ao DE através da estrutura [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md) Essas informações adicionais incluem o ID do fornecedor do DE (na forma de um GUID), o nome de um ponto de rastreamento e o nome de uma restrição de ponto de ruptura.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
