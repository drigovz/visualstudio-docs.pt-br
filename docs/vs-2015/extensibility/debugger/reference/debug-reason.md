---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95a537c703d4afd68bb291205e0c7da8d9b8fc59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143019"
---
# <a name="debug_reason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica por que o processo foi iniciado para depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 DEBUG_REASON_ERROR  
 Ocorreu um erro não específico (isso é usado como uma condição padrão quando nenhum dos outros motivos se ajusta).  
  
 DEBUG_REASON_USER_LAUNCHED  
 O processo foi iniciado na solicitação do usuário.  
  
 DEBUG_REASON_USER_ATTACHED  
 O processo que já estava em execução foi anexado ao usuário.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 O processo foi anexado automaticamente quando foi iniciado.  
  
 DEBUG_REASON_CAUSALITY  
 O processo foi iniciado devido a um evento de depuração JIT ( *just-in-time* ).  
  
## <a name="remarks"></a>Comentários  
 Retornado do método [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
