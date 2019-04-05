---
title: IDebugBreakpointRequest2::GetLocationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2::GetLocationType
helpviewer_keywords:
- IDebugBreakpointRequest2::GetLocationType
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef335232b20fbc74c323fe96ab283280e9d2aad6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926288"
---
# <a name="idebugbreakpointrequest2getlocationtype"></a>IDebugBreakpointRequest2::GetLocationType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o tipo de local de ponto de interrupção dessa solicitação de ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetLocationType(   
   BP_LOCATION_TYPE* pBPLocationType  
);  
```  
  
```csharp  
int GetLocationType(   
   out enum_BP_LOCATION_TYPE pBPLocationType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBPLocationType`  
 [out] Retorna um valor da [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) enumeração que descreve o local dessa solicitação de ponto de interrupção.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_FAIL` se o `bpLocation` campo associado [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estrutura não é válida.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CDebugBreakpointRequest` objeto que expõe o[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interface.  
  
```  
HRESULT CDebugBreakpointRequest::GetLocationType(BP_LOCATION_TYPE* pBPLocationType)    
{    
   HRESULT hr;    
  
   if (pBPLocationType)    
   {    
      // Set default BP_LOCATION_TYPE.    
      *pBPLocationType = BPLT_NONE;    
  
      // Check if the BPREQI_BPLOCATION flag is set in BPREQI_FIELDS.    
      if (IsFlagSet(m_bpRequestInfo.dwFields, BPREQI_BPLOCATION))    
      {    
         // Get the new BP_LOCATION_TYPE.    
         *pBPLocationType = m_bpRequestInfo.bpLocation.bpLocationType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
