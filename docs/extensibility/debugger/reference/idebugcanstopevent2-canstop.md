---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734595"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica o motor de depuração (DE) se deve ou não parar no local de código atual ou apenas continuar a execução.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>parâmetros
`fCanStop`\
[em] Não-zero`TRUE`( ) se o DE parar no local de código atual; caso contrário,`FALSE`zero ( ).

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O receptor deste evento normalmente chama o método [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) para determinar a `IDebugCanStopEvent2::CanStop` razão pela qual o DE quer parar e, em seguida, chama o método com a resposta apropriada.

 Se o DE parar, ele envia um evento que descreve o motivo para parar. Normalmente, há dois eventos que são enviados, uma quebra de usuário ou sinal representada pela interface [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) e um evento de breakpoint representado pela interface [IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

## <a name="see-also"></a>Confira também
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
