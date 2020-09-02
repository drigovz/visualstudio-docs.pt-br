---
title: 'IDebugPendingBreakpoint2:: virtualizar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Virtualize
helpviewer_keywords:
- Virtualize method
- IDebugPendingBreakpoint2::Virtualize method
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf4277afc63d403cc3d02c4d79b9e5f2b1b8d26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143884"
---
# <a name="idebugpendingbreakpoint2virtualize"></a>IDebugPendingBreakpoint2::Virtualize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Alterna o estado virtualizado deste ponto de interrupção pendente. Quando um ponto de interrupção pendente é virtualizado, o mecanismo de depuração tentará associá-lo toda vez que um novo código for carregado no programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp#  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fVirtualize`  
 no Defina como diferente de zero ( `TRUE` ) para virtualizar o ponto de interrupção pendente ou para zero ( `FALSE` ) para desativar a virtualização.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o ponto de interrupção foi excluído.  
  
## <a name="remarks"></a>Comentários  
 Um ponto de interrupção virtualizado é associado toda vez que o código é carregado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um `CPendingBreakpoint` objeto simples que expõe a interface [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
```cpp#  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
