---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac5fafb3e89ed414fd64843e4f6336127d9665a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917126"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando um programa é anexado ao.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O fornecedor de porta personalizada ou DE implementa essa interface para relatar que um programa tiver sido criado, normalmente no momento em que o programa é anexado ao. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface. O SDM usa o `QueryInterface` método para acessar o `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 O fornecedor de porta personalizada ou DE cria e envia esse objeto de evento para a criação de um programa de relatório. O DE envia esse evento usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando anexado a programa que está sendo depurado. O fornecedor de porta personalizada envia esse evento usando o [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interface.

## <a name="remarks"></a>Comentários
 O fornecedor de porta personalizada ou DE publica uma nova [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface chamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)