---
title: 'IDebugCanStopEvent2:: canpare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8167013489b3b37e254100f7547cd61d54529b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191192"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Notifica o mecanismo de depuração (DE) se deseja ou não parar no local do código atual ou apenas continuar a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fCanStop`  
 no Diferente de zero ( `TRUE` ) se o de deve parar no local do código atual; caso contrário, zero ( `FALSE` ).  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O receptor desse evento normalmente chama o método [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) para determinar o motivo pelo qual o deseja parar e, em seguida, chama o `IDebugCanStopEvent2::CanStop` método com a resposta apropriada.  
  
 Se o DE for interrompido, ele enviará um evento que descreve o motivo da interrupção. Normalmente, há dois eventos que são enviados, um usuário ou uma quebra de sinal representada pela interface [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) e um evento de ponto de interrupção representado pela interface [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
