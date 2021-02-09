---
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcf8a827f09c1b8d0e83b92f7729635cbb0f7f18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896169"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Esse método envia eventos que significam a criação e a destruição de processos e programas em uma porta.

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

## <a name="parameters"></a>Parâmetros
`pMachine`\
no Um objeto [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que representa o servidor de depuração (há um para cada instância do [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ) em que o evento ocorreu.

`pPort`\
no Um objeto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa a porta na qual o evento ocorreu.

`pProcess`\
no Um objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa o processo no qual o evento ocorreu.

`pProgram`\
no Um objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa no qual o evento ocorreu.

`pEvent`\
no Um objeto [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que identifica o evento. Os eventos possíveis são os seguintes:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
no O GUID do evento. Como o evento é convertido em [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) antes de chamar esse método, esse identificador torna mais fácil determinar qual evento está sendo enviado.

## <a name="return-value"></a>Valor de retorno
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
