---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65edef6585fd8367c6fb23c291bf4e8376de8861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153355"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contém as informações necessárias para implementar um ponto de interrupção, incluindo GUID do fornecedor, restrição e tracepoint.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```csharp  
public struct BP_REQUEST_INFO2 {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
};  
```  
  
## <a name="members"></a>Membros  
 `dwFields`  
 Uma combinação de sinalizadores da enumeração [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) que especifica quais campos são preenchidos.  
  
 `guidLanguage`  
 O GUID do idioma.  
  
 `bpLocation`  
 A estrutura de [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) que especifica o tipo do local do ponto de interrupção.  
  
 `pProgram`  
 O objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o aplicativo no qual ocorre o ponto de interrupção.  
  
 `bstrProgramName`  
 O nome do aplicativo no qual ocorre o ponto de interrupção.  
  
 `pThread`  
 O objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o thread no qual o ponto de interrupção ocorre.  
  
 `bstrThreadName`  
 O nome do thread no qual o ponto de interrupção ocorre.  
  
 `bpCondition`  
 A estrutura de [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que descreve as condições sob as quais o ponto de interrupção será acionado.  
  
 `bpPassCount`  
 A estrutura de [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que contém as informações de contagem de aprovação do ponto de interrupção.  
  
 `dwFlags`  
 Uma combinação de sinalizadores da enumeração [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) que especifica os sinalizadores para o ponto de interrupção solicitado.  
  
 `guidVendor`  
 GUID do fornecedor. Pode ser um valor nulo.  
  
 `bstrConstraint`  
 Nome da restrição de ponto de interrupção. Pode ser um valor nulo.  
  
 `bstrTracepoint`  
 Nome do ponto de rastreamento. Pode ser um valor nulo.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada pelo método [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
