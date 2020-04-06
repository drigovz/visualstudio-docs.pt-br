---
title: IDebugThreadCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadCreateEvent2
helpviewer_keywords:
- IDebugThreadCreateEvent2
ms.assetid: aee34a14-4f9c-4ad3-845f-c96ee938cefd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1aaa25e719f17701344d821759a0dac06aa88698
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718531"
---
# <a name="idebugthreadcreateevent2"></a>IDebugThreadCreateEvent2
Esta interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de depuração de sessão (SDM) quando um segmento é criado em um programa que está sendo depurado.

## <a name="syntax"></a>Sintaxe

```
IDebugThreadCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa esta interface para informar que um segmento foi criado. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que esta interface. O SDM usa [queryInterface](/cpp/atl/queryinterface) para acessar a `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE cria e envia esse objeto de evento para informar que um segmento foi criado. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando é anexada ao programa que está sendo depurado.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
