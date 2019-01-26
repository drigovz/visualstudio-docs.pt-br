---
title: IEnumDebugPorts2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3586e3aefa38b7c8a49b693df86c3241a39d194
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916098"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
Ignora o número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Número de elementos a serem ignorados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se `celt` é maior que o número de elementos restantes; caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se `celt` Especifica um valor maior que o número de elementos restantes, a enumeração é definida como o fim e `S_FALSE` é retornado.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)