---
title: IEnumDebugFields::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 152405f8a3bc5b81724f37848b7d356afa866860
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931008"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
Esse método retorna o próximo conjunto de elementos da enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
   ULONG         celt,  
   IDebugField** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint          celt,  
   IDebugField[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de elementos a serem recuperados. Também especifica o tamanho máximo da `rgelt` matriz.  
  
 `rgelt`  
 [no, out] Matriz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) elementos a serem preenchidos.  
  
 `pceltFetched`  
 [out] Retorna o número de elementos realmente retornados em `rgelt`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)