---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716888"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Esta interface enumera os pontos de interrupção de erro associados a um ponto de interrupção pendente.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface como parte de seu suporte para pontos de interrupção.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [o CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) para obter essa interface representando uma lista de pontos de interrupção que não podem ser vinculados, ou [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) para obter essa interface representando uma lista de pontos de interrupção que não foram vinculados.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugErrorBreakpoints2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera um número especificado de pontos de interrupção de erro em uma seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Salta um número especificado de pontos de interrupção de erro em uma seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Obtém o número de pontos de interrupção de erro em um enumerador.|

## <a name="remarks"></a>Comentários
 Esta interface contém uma lista de interfaces [IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) cada uma das quais descreve um ponto de ruptura que não poderia ser vinculado e por que não poderia ser vinculado. O Visual `IEnumDebugErrorBreakpoint2` Studio usa a interface para atualizar os pontos de interrupção mostrados no IDE.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
