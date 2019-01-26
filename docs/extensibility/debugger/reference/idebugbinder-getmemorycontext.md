---
title: IDebugBinder::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb90a9688f44c20a99292a1901812d8c3fbab64d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916323"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Esse método converte um local do objeto ou um endereço de memória em um contexto de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pField`  
 [in] Uma [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que descreve o objeto a ser localizado. Se `NULL`, em seguida, use `dwConstant` em vez disso.  
  
 `dwConstant`  
 [in] Um endereço de memória constante, como 0x5000.  
  
 `ppMemCxt`  
 [out] Retorna o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface que representa o endereço do objeto ou o endereço na memória.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)