---
title: IDebugArrayField::GetElementType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6daf0fc7a7aa2f283728210003254885345d69ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954794"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Obtém o tipo de elemento na matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppType`  
 [out] Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que descreve o tipo de elemento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) objeto pressupõe que todos os elementos da matriz são do mesmo tipo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)