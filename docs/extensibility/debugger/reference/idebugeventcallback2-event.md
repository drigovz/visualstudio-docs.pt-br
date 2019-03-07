---
title: IDebugEventCallback2::Event | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 461c2487c18cb6edc5601868c0f9644d7b8eeac1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686958"
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

#### <a name="parameters"></a>Parâmetros
 `pEngine`

 [in] Uma [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa o mecanismo de depuração (DES) que está enviando esse evento. A DE é necessário para preencher esse parâmetro.

 `pProcess`

 [in] Uma [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa o processo no qual o evento ocorre. Esse parâmetro é preenchido pelo Gerenciador de depuração de sessão (SDM). A DE sempre passa um valor nulo para esse parâmetro.

 `pProgram`

 [in] Uma [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa em que esse evento ocorre. Para a maioria dos eventos, esse parâmetro não é um valor nulo.

 `pThread`

 [in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread no qual esse evento ocorre. Para interromper eventos, esse parâmetro não pode ser um valor nulo como o quadro de pilha é obtido desse parâmetro.

 `pEvent`

 [in] Uma [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que representa o evento de depuração.

 `riidEvent`

 [in] GUID que identifica qual interface de eventos para obter do `pEvent` parâmetro.

 `dwAttrib`

 [in] Uma combinação de sinalizadores do [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumeração.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Ao chamar esse método, o `dwAttrib` parâmetro deve corresponder ao valor retornado do [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) método como chamado no objeto de evento passado a `pEvent` parâmetro.

 Todos os eventos de depuração são lançados de forma assíncrona, independentemente se um evento em si é assíncrono ou não. Quando a DE chama esse método, o valor de retorno não indica se o evento foi processado, apenas se o evento foi recebido. Na verdade, na maioria das circunstâncias, o evento não foi processado quando este método retorna.

## <a name="see-also"></a>Consulte também
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)