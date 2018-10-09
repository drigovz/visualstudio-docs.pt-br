---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3bd02b6f2990ebce9ecd7774938dd276fb26ab4d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466302"
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [BP_ERROR_RESOLUTION_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-error-resolution-info).  
  
Descreve a resolução de um ponto de interrupção de erro, incluindo local, o programa e o thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>Membros  
 `dwFields`  
 Uma combinação de valores de [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) enumeração que especifica quais campos dessa estrutura são preenchidos.  
  
 `bpResLocation`  
 O [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) união, que especifica o local de resolução de ponto de interrupção.  
  
 `pProgram`  
 O [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o aplicativo no qual ocorreu o erro de ponto de interrupção.  
  
 `pThread`  
 O [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está executando o aplicativo que gerou o erro de ponto de interrupção.  
  
 `bstrMessage`  
 Uma cadeia de caracteres que contém qualquer mensagem de aviso ou erro resultantes dessa resolução de erro.  
  
 `dwType`  
 Um valor a partir de [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) enumeração que especifica o tipo de erro de ponto de interrupção.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada a partir de [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
