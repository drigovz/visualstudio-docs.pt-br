---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734517"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Esta interface é usada para perguntar ao Gerenciador de depuração de sessão (SDM) se deve parar no local de código atual.

## <a name="syntax"></a>Sintaxe

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para suportar a passagem através do código-fonte. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que esta interface (o SDM usa [queryInterface](/cpp/atl/queryinterface) para acessar a `IDebugEvent2` interface).

 A implementação desta interface deve comunicar a chamada do SDM do [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) para o mecanismo de depuração. Por exemplo, isso pode ser feito com uma mensagem postada no segmento de manuseio de mensagens do mecanismo de depuração ou o objeto que `IDebugCanStopEvent2::CanStop`implementa esta interface pode conter uma referência ao mecanismo de depuração e chamar de volta para o mecanismo de depuração com o sinalizador passado para .

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE pode enviar este método cada vez que o DE é solicitado a continuar a execução e o DE está pisando através do código. Este evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornecida pelo SDM quando anexada ao programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugCanStopEvent2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Fica a razão para este evento.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Especifica se o programa que está sendo depurado deve parar no local deste evento (e enviar um evento que descreve o motivo da parada) ou apenas continuar a execução.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtém o contexto do documento que descreve a localização deste evento.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtém o contexto de código que descreve a localização deste evento.|

## <a name="remarks"></a>Comentários
 O DE envia essa interface se o usuário entrar em uma função e o DE não encontrar informações de depuração lá ou depurar informações, mas o DE não sabe se o código-fonte pode ser exibido para esse local.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
