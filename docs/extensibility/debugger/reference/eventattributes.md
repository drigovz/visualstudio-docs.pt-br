---
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737063"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Especifica os atributos do evento.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Campos
`EVENT_ASYNCHRONOUS`\
Indica que o evento é assíncrono e nenhuma resposta ao evento é necessária.

`EVENT_SYNCHRONOUS`\
Indica que o evento é síncrono; responder por meio de [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indica que este é um evento de parada. Deve ser combinado `EVENT_ASYNCHRONOUS` com `EVENT_SYNCHRONOUS`qualquer um ou .

`EVENT_ASYNC_STOP`\
Indica um evento de parada assíncrona. No momento, não existe tal evento. Esta bandeira é apenas um espaço reservado.

`EVENT_SYNC_STOP`\
Indica um evento de parada `EVENT_SYNCHRONOUS` síncrono (uma combinação de e `EVENT_STOPPING`). Este valor é usado por um motor de depuração (DE) quando envia um evento de parada. A resposta é feita por meio de uma chamada para [Executar,](../../../extensibility/debugger/reference/idebugprogram2-execute.md) [Passo](../../../extensibility/debugger/reference/idebugprogram2-step.md)ou [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indica um evento que é enviado imediatamente e sincronicamente para o IDE. Esta bandeira é combinada com `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`outras `EVENT_SYNC_STOP` bandeiras como , ou para indicar o tipo de evento e o fato de que o mecanismo de resposta (se houver) é conhecido.

`EVENT_EXPRESSION_EVALUATION`\
O evento é resultado da avaliação de expressão.

## <a name="remarks"></a>Comentários
Esses valores são `dwAttrib` passados no parâmetro do método [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
