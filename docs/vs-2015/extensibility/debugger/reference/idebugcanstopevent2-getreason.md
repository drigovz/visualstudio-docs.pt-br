---
title: 'IDebugCanStopEvent2:: GetReason | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191147"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o motivo pelo qual o mecanismo de depuração (DE) deseja parar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcr`  
 fora Retorna um valor da enumeração [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) que descreve o motivo para esse evento.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é normalmente chamado antes do método [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) , para que o chamador possa determinar se deve passar um valor diferente de zero ( `TRUE` ) para o `IDebugCanStopEvent2::CanStop` método.  
  
 O motivo da interrupção pode ser `CANSTOP_ENTRYPOINT` , ou seja, o de atingiu um ponto de entrada ou `CANSTOP_STEPIN` , o que significa que o de foi dividido em uma função.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
