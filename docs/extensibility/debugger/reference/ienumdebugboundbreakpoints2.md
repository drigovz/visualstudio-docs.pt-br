---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717447"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Essa interface enumera os pontos de interrupção vinculados associados a um ponto de interrupção ou evento associado de ponto de interrupção pendente.

## <a name="syntax"></a>Syntax

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para pontos de interrupção. Essa interface deve ser implementada se houver suporte a pontos de interrupção.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chamadas do Visual Studio:

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obter essa interface que representa uma lista de todos os pontos de interrupção que foram disparados.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para obter essa interface representando uma lista de todos os pontos de interrupção que foram associados.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) para obter essa interface representando uma lista de todos os pontos de interrupção associados a esse ponto de interrupção pendente.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IEnumDebugBoundBreakpoints2` .

|Método|Descrição|
|------------|-----------------|
|[Próximo](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera um número especificado de pontos de interrupção associados em uma sequência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignora um número especificado de pontos de interrupção associados em uma sequência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Obtém o número de pontos de interrupção associados em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa os pontos de interrupção associados representados por essa interface para atualizar a exibição de pontos de interrupção no IDE.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
