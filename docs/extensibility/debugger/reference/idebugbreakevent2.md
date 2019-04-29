---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdefbfa71ed220eed6e3f32ee95c02197f58a85d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923420"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Essa interface informa o Gerenciador de sessão de depuração (SDM) que a interrupção assíncrona foi concluída com êxito.

## <a name="syntax"></a>Sintaxe

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O DE implementa essa interface para dar suporte a quebras de usuário em um programa. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface (usa o SDM [QueryInterface](/cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface).

## <a name="notes-for-callers"></a>Observações para chamadores
 As chamadas SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando o usuário solicitou o programa que está sendo depurado para ser pausado. Quando o programa foi pausado com êxito, o DE envia o `IDebugBreakEvent2` eventos. Esse evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada fornecida pelo SDM quando anexado a programa que está sendo depurado.

## <a name="remarks"></a>Comentários
 Por exemplo, um usuário pode selecionar o **interromper tudo** comando as **depurar** menu Sair de um programa que está executando um loop infinito. O SDM informa o programa parar, chamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). O envia DE `IDebugBreakEvent2` quando o programa é interrompido por último.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)