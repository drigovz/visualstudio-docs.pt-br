---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95706df8b9b4d366e8baf25a96e3e15bc6532be1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930206"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Especifica os critérios para comparar dois contextos de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Membros  
 CONTEXT_EQUAL  
 Localize o contexto de memória primeiro na lista que é igual ao contexto de memória de destino.  
  
 CONTEXT_LESS_THAN  
 Localize o contexto de memória primeiro na lista que é menor que o contexto de memória de destino.  
  
 CONTEXT_GREATER_THAN  
 Localize o contexto de memória primeiro na lista que é maior que o contexto de memória de destino.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Localize o contexto de memória primeiro na lista que é menor ou igual ao contexto de memória de destino.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Localize o contexto de memória primeiro na lista que é maior que ou igual ao contexto de memória de destino.  
  
 CONTEXT_SAME_SCOPE  
 Localize o contexto de memória primeiro na lista que está no mesmo escopo que o contexto de memória de destino.  
  
 CONTEXT_SAME_FUNCTION  
 Localize o contexto de memória primeiro na lista que está na mesma função que o escopo de memória de destino.  
  
 CONTEXT_SAME_MODULE  
 Localize o contexto de memória primeiro na lista que está no mesmo módulo como o contexto de memória de destino.  
  
 CONTEXT_SAME_PROCESS  
 Localize o contexto de memória primeiro na lista que está no mesmo processo que o contexto de memória de destino.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) método.  
  
 Esses valores são usados para localizar o contexto de memória primeiro em uma lista que satisfaz os critérios de comparação especificado. Um contexto de memória é dada uma lista de contextos de memória para comparar a próprio em relação a por meio de `IDebugMemoryContext2::Compare` método. O contexto de memória primeiro na lista para o qual o operador de comparação é `true` , em seguida, será retornado.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)