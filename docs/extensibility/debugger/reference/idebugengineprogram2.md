---
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730303"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Esta interface oferece suporte de depuração de vários segmentos.

## <a name="syntax"></a>Sintaxe

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um mecanismo de depuração implementa essa interface para suportar a depuração simultânea de vários segmentos. Esta interface é implementada no mesmo objeto que implementa a interface [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [queryInterface](/cpp/atl/queryinterface) para obter `IDebugProgram2` esta interface a partir de uma interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugEngineProgram2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Interrompe todos os segmentos que estão sendo executados neste programa.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Observa para que a execução (ou pare de observar a execução) ocorra no segmento dado.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permite (ou não permite) que a avaliação de expressão ocorra no segmento dado, mesmo que o programa seja interrompido.|

## <a name="remarks"></a>Comentários
 O Visual Studio chama essa interface em resposta a um evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e para definir os estados "Watch for Thread Step" e "Watch for Expression Evaluation on Thread" do programa. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) é chamado sempre que o programa deve ser interrompido; este método dá ao programa a chance de terminar todos os segmentos.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
