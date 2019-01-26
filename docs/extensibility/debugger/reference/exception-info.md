---
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e255695cd461f5c272bc65f695d8935ab892d034
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960237"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Descreve uma exceção ou erro de tempo de execução gerado pelo programa que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Membros  
 pProgram  
 O [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa no qual a exceção ocorreu.  
  
 bstrProgramName  
 O nome do programa no qual a exceção ocorreu.  
  
 bstrExceptionName  
 O nome da exceção.  
  
 dwCode  
 O código de identificação para o erro de exceção ou tempo de execução.  
  
 dwState  
 Um valor a partir de [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) enumeração que define o estado da exceção.  
  
 guidType  
 O identificador de idioma GUID, seja `guidLang` ou `guidEng`.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada como um parâmetro para o [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) e o [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) métodos. Essa estrutura também é passada para o [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) método a ser preenchido.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)