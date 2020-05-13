---
title: IDebugPortEvents2::Evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725239"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Esse método envia eventos que significam a criação e destruição de processos e programas em um porto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>parâmetros
`pMachine`\
[em] Um objeto [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que representa o servidor de depuração (há um para cada instância de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) em que o evento ocorreu.

`pPort`\
[em] Um objeto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa a porta em que o evento ocorreu.

`pProcess`\
[em] Um objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa o processo em que o evento ocorreu.

`pProgram`\
[em] Um objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa em que o evento ocorreu.

`pEvent`\
[em] Um objeto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que identifica o evento. Os possíveis eventos são os seguintes:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[em] O GUID do evento. Como o evento é lançado para [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) antes de chamar esse método, este identificador facilita a determinação de qual evento está sendo enviado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
