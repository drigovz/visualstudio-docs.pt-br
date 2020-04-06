---
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718585"
---
# <a name="idebugthread2"></a>IDebugThread2
Esta interface representa um segmento em execução em um programa.

## <a name="syntax"></a>Sintaxe

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa esta interface para representar um segmento de execução em um único programa.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para [getThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) para obter esta interface representando o segmento ativo no momento.

 Esta interface também é usada na criação de uma solicitação de ponto de ruptura (veja [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Esta interface também é retornada ao resolver um ponto de ruptura de limite ou erro (ver [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) e [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugThread2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera uma lista dos quadros de pilha para este segmento.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Fica com o nome do fio.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Define o nome do segmento.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Recebe o programa em que um fio está sendo executado.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina se a próxima declaração pode ser definida como o determinado quadro de pilha e o contexto de código.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Define a próxima declaração para o determinado quadro de pilha e o contexto de código.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtém o identificador de rosca do sistema.|
|[Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Suspende um fio.|
|[Continuar](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Retoma um fio.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Obtém propriedades que descrevem um fio.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtém o fio lógico associado a este fio físico.|

## <a name="remarks"></a>Comentários
 Como um único segmento físico pode ser executado `IDebugThread2` em vários programas, mais de um de mais de um programa pode representar o mesmo segmento físico.

 Quando ocorre um ponto de ruptura ou exceção, um evento é enviado chamando [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Um dos argumentos para este `IDebugThread2` método é uma interface representando o segmento atual. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) é usado para obter a interface [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para o quadro de pilha atual.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
