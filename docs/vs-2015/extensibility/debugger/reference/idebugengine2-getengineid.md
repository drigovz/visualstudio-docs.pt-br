---
title: IDebugEngine2::GetEngineID | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 645092f5a9f72e3da086a2d53b86a18e6f3ff659
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835950"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o GUID do mecanismo de depuração (DES).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pguidEngine`  
 [out] Retorna o GUID do DE.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Alguns exemplos de GUIDs típicos `guidScriptEng`, `guidNativeEng`, ou `guidSQLEng`. Novos mecanismos de depuração criará seu próprio GUID para identificação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um simples `CEngine` objeto que implementa o [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface.  
  
```cpp#  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

