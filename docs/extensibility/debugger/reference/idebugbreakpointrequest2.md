---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734919"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Esta interface representa as informações necessárias para criar e vincular qualquer tipo de ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O SDM (Session Debug Manager, gerenciador de depuração de sessão) normalmente implementa essa interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 O mecanismo de depuração (DE) recebe essa interface através de uma chamada para [CreatePendingBreakpoint,](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) a fim de criar um breakpoint pendente. Uma chamada para [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) pode recuperar esta interface do DE.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugBreakpointRequest2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtém o tipo de localização de ponto de ruptura desta solicitação de ponto de ruptura.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtém as informações de solicitação de ponto de ruptura que descrevem essa solicitação de ponto de ruptura.|

## <a name="remarks"></a>Comentários
 Depois que o programa está sendo depurado, uma chamada para [Vincular vincula](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) um ponto de ruptura pendente ao local solicitado no programa.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
