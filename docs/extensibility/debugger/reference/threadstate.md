---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d980eda1cb876392342e8eef7c49ec68456c8908
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951063"
---
# <a name="threadstate"></a>THREADSTATE
Especifica o estado do thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Membros  
 THREADSTATE_RUNNING  
 Indica que o thread está em execução.  
  
 THREADSTATE_STOPPED  
 Indica que o thread é interrompido devido a um ponto de interrupção.  
  
 THREADSTATE_FRESH  
 Indica que o thread foi criado, mas ainda não está executando o código.  
  
 THREADSTATE_DEAD  
 Indica que o thread está inativo.  
  
 THREADSTATE_FROZEN  
 Indica que o thread está congelado (nenhuma execução pode ser executada).  
  
## <a name="remarks"></a>Comentários  
 Usado para o `dwThreadState` campo do [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)