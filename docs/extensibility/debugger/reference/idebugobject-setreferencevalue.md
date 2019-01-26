---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd1c00dc1ecd3f90c3dce6f9526957c462303451
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004416"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Define o valor de referência do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pObject`  
 [in] Uma [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa o novo valor de referência.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método faz isso [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto uma referência para o valor do objeto fornecido no `pObject` parâmetro, descartando qualquer referência anterior. Observe que este `IDebugObject` objeto já deve ser um tipo de referência.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)