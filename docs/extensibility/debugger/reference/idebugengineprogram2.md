---
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb608d834f50ca5f778d653b5733395b7c2cb12f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038325"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Essa interface fornece suporte de depuração com multithread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um mecanismo de depuração implementa essa interface para dar suporte à depuração simultânea de vários threads. Essa interface é implementada no mesmo objeto que implementa o [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](/cpp/atl/queryinterface) para obter essa interface de um `IDebugProgram2` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugEngineProgram2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Interrompe todos os threads em execução nesse programa.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Procura de execução (ou assistir a execução de parada) para ocorrer em determinado thread.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permite (ou não) a avaliação da expressão para ocorrer em determinado thread, mesmo se o programa for interrompido.|  
  
## <a name="remarks"></a>Comentários  
 Visual Studio chama essa interface em resposta a um [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos e definir os estados "Inspeção de etapa de Thread" e "Inspeção para expressão de avaliação no Thread" do programa. [Parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) é chamado sempre que o programa deve ser interrompida; esse método permite que o programa a oportunidade de se encerrar todos os threads.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)