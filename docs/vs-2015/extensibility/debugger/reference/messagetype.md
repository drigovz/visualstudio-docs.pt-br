---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547202"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica o tipo e o motivo da mensagem.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Membros  
 MT_OUTPUTSTRING  
 Indica que a mensagem deve ser enviada para a janela de saída. Isso é mutuamente exclusivo do `MT_MESSAGEBOX` .  
  
 MT_MESSAGEBOX  
 Indica que a mensagem deve ser mostrada em uma caixa de mensagem. Isso é mutuamente exclusivo do `MT_OUTPUTSTRING` .  
  
 MT_TYPE_MASK  
 Um valor de máscara para isolar o destino da mensagem.  
  
 MT_REASON_EXCEPTION  
 Indica que uma caixa de mensagem está sendo mostrada como resultado de uma exceção. Isso é mutuamente exclusivo do `MT_REASON_TRACEPOINT` .  
  
 MT_REASON_TRACEPOINT  
 Indica que uma caixa de mensagem está sendo mostrada como resultado de atingir um tracepoint. Isso é mutuamente exclusivo para `MT_REASON_EXCEPTION` .  
  
 MT_REASON_MASK  
 Um valor de máscara para isolar o motivo da mensagem que está sendo mostrada.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são retornados dos métodos [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .  
  
 Um dos valores de motivo pode ser combinado com um dos valores de destino de saída usando um bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
