---
title: THREADPROPERTY_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204803"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica quais informações sobre um thread deve ser recuperado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 TPF_ID  
 Inicialização/usar o `dwThreadId` campo do [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estrutura.  
  
 TPF_SUSPENDCOUNT  
 Inicialização/usar o `dwSuspendCount` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_STATE  
 Inicialização/usar o `dwThreadState` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_PRIORITY  
 Inicialização/usar o `bstrPriority` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_NAME  
 Inicialização/usar o `bstrName` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_LOCATION  
 Inicialização/usar o `bstrLocation` campo do `THREADPROPERTIE`estrutura.  
  
 TPF_ALLFIELDS  
 Especifica todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados como um argumento para o [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método para indicar quais campos da [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) são de estrutura a ser inicializado.  
  
 Esses valores também são usados no `dwFields` membro o `THREADPROPERTIES` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
