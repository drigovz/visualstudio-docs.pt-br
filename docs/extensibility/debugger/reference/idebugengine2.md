---
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730855"
---
# <a name="idebugengine2"></a>IDebugEngine2
Esta interface representa um mecanismo de depuração (DE). Ele é usado para gerenciar vários aspectos de uma sessão de depuração, desde a criação de pontos de interrupção até a definição e a compensação de exceções.

## <a name="syntax"></a>Sintaxe

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada por um DE personalizado para gerenciar a depuração de programas. Esta interface deve ser implementada pelo DE.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é chamada pelo SDM (Session Debug Manager, gerenciador de depuração) para gerenciar a sessão de depuração, incluindo gerenciamento de exceções, criação de pontos de interrupção e resposta a eventos síncronos enviados pelo DE.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugEngine2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Cria um enumerador para todos os programas que estão sendo depurados por um DE.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Anexa um DE a um programa.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Cria um ponto de ruptura pendente no DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica como o DE deve lidar com uma determinada exceção.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Remove a exceção especificada para que não seja mais manuseada pelo motor de depuração.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Remove a lista de exceções definidas pelo IDE para uma arquitetura ou idioma em tempo de execução específico.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Recebe o GUID do DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a a de que o programa especificado foi atipicamente encerrado e que o DE deve limpar todas as referências ao programa e enviar um evento de destruição do programa.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chamado pelo SDM para indicar que um evento de depuração síncrona, anteriormente enviado pelo DE ao SDM, foi recebido e processado.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Define a localidade do DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Define a raiz de registro atualmente em uso pelo DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Define uma métrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Solicita que todos os programas que estão sendo depurados por este DE interrompam a execução na próxima vez que um de seus threads tentar ser executado.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
