---
title: IDebugEventCallback2::Evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729899"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envia notificação de eventos de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>parâmetros
`pEngine`\
[em] Um objeto [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) que representa o mecanismo de depuração (DE) que está enviando este evento. Um DE é necessário para preencher este parâmetro.

`pProcess`\
[em] Um objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa o processo em que o evento ocorre. Este parâmetro é preenchido pelo gerenciador de depuração de sessão (SDM). Um DE sempre passa um valor nulo para este parâmetro.

`pProgram`\
[em] Um objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa em que este evento ocorre. Para a maioria dos eventos, este parâmetro não é um valor nulo.

`pThread`\
[em] Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o segmento no qual esse evento ocorre. Para eventos de interrupção, este parâmetro não pode ser um valor nulo, pois o quadro de pilha é obtido a partir deste parâmetro.

`pEvent`\
[em] Um objeto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que representa o evento de depuração.

`riidEvent`\
[em] GUID que identifica qual interface de `pEvent` evento obter a partir do parâmetro.

`dwAttrib`\
[em] Uma combinação de bandeiras da enumeração [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Ao chamar este `dwAttrib` método, o parâmetro deve corresponder ao valor retornado do método [GetAttributes,](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) conforme chamado no objeto de evento passado no `pEvent` parâmetro.

 Todos os eventos de depuração são postados assíncronamente, independentemente de um evento em si ser assíncrono ou não. Quando um DE chama esse método, o valor de devolução não indica se o evento foi processado, apenas se o evento foi recebido. Na verdade, na maioria das circunstâncias, o evento não foi processado quando este método retorna.

## <a name="see-also"></a>Confira também
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
