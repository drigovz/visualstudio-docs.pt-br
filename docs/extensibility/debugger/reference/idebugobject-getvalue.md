---
title: IDebugObject::GetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98dd9208fe28fd433a201e4d59f8dcc0af694b08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914150"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtém o valor do objeto consecutivos de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pValue`  
 [no, out] Uma matriz que é preenchida com uma série consecutiva de bytes que representa o valor do objeto.  
  
 `nSize`  
 [in] O número máximo de bytes para buscar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Obter o número total de bytes do valor que pode ser buscadas chamando o [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)