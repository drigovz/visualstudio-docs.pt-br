---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926738"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descreve as propriedades de um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Membros  
 dwFields  
 Uma combinação de sinalizadores do [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumeração, que descreve quais campos nessa estrutura são válidos.  
  
 dwThreadId  
 A ID do thread.  
  
 dwSuspendCount  
 Contagem de suspensões do thread.  
  
 dwThreadState  
 Um valor a partir de [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) enumeração que indica o estado do thread operacional.  
  
 bstrPriority  
 Uma cadeia de caracteres que especifica a prioridade de thread; Por exemplo, "Acima do Normal", "Normal" ou "Tempo crítico".  
  
 bstName  
 O nome do thread.  
  
 bstrLocation  
 O local de thread (normalmente, o quadro de pilha mais alto), geralmente expressado como o nome do método em que a execução é interrompida no momento.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é preenchida por uma chamada para o [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método. As informações retornadas então normalmente são usadas no preenchimento de **Threads** janela.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
