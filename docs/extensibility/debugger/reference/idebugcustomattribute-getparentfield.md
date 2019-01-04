---
title: IDebugCustomAttribute::GetParentField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f0165c5a60b79ba5a23cb9e14a1d917058ad200
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916686"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Obtém o campo ao qual o atributo personalizado está anexado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppField`  
 [out] Retorna o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa o campo ao qual o atributo personalizado está anexado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame o [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método em retornado [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) é de objeto para determinar qual tipo de campo pai.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)