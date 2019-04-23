---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7abba929e6c146e322147555dc750e2fc66ac9e8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041502"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Essa interface enumera os pontos de interrupção associados associados com um ponto de interrupção pendente ou ponto de interrupção associado a eventos.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface como parte de seu suporte para pontos de interrupção. Essa interface deve ser implementada, se houver suporte para os pontos de interrupção.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama:

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obter essa interface que representa uma lista de todos os pontos de interrupção que foram acionadas.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para obter essa interface que representa uma lista de todos os pontos de interrupção que foram ligados.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) para obter essa interface que representa uma lista de todos os pontos de interrupção associada a esse ponto de interrupção pendente.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IEnumDebugBoundBreakpoints2`.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera um número especificado de pontos de interrupção associados em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignora um número especificado de pontos de interrupção associada em uma sequência de enumeração.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Obtém o número de pontos de interrupção associada em um enumerador.|

## <a name="remarks"></a>Comentários
 Visual Studio usa os pontos de interrupção associados, representados por esta interface para atualizar a exibição de pontos de interrupção no IDE.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)