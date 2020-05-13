---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725645"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Esta interface representa um ponto de ruptura que está pronto para se ligar a um local de código.

## <a name="syntax"></a>Sintaxe

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para pontos de interrupção.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) cria um ponto de ruptura pendente a partir de uma interface [IDebugBreakpointRequest2.](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Uma chamada [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) para `IDebugBreakpoint2` Bind cria uma interface que representa um ponto de ruptura vinculado no programa.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugPendingBreakpoint2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se esse ponto de ruptura pendente pode se ligar a um local de código.|
|[Associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Vincula este ponto de ruptura pendente a um ou mais locais de código.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Fica com o estado deste ponto de ruptura pendente.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Recebe o pedido de ponto de ruptura que foi usado para criar este ponto de ruptura pendente.|
|[Virtualizar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alterna o estado virtualizado deste ponto de ruptura pendente.|
|[Habilitar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna o estado habilitado deste ponto de ruptura pendente.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Define ou altera a condição associada a este ponto de ruptura pendente.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Define ou altera a contagem de passes associada a este ponto de ruptura pendente.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos os breakpoints ligados a partir deste breakpoint pendente.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos os pontos de interrupção de erro resultantes deste breakpoint pendente.|
|[Excluir](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Exclui este ponto de interrupção pendente e todos os pontos de interrupção vinculados a partir dele.|

## <a name="remarks"></a>Comentários
 `IDebugPendingBreakpoint2`pode ser considerado como um provedor de todas as informações necessárias para vincular um ponto de ruptura ao código que pode ser aplicado a um ou muitos programas.

 Um ponto de ruptura pendente pode potencialmente produzir mais de um ponto de ruptura vinculado. Por exemplo, um ponto de ruptura em um modelo de estilo C++poderia produzir um ponto de ruptura vinculado para cada instância única desse modelo.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
