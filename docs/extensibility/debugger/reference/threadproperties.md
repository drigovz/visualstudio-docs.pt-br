---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59b0fd83202ea8a5514d1ed637404d4864bf6b57
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460720"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Descreve as propriedades de um thread.

## <a name="syntax"></a>Sintaxe

```cpp
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
 `dwFields`\
 Uma combinação de sinalizadores do [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumeração, que descreve quais campos nessa estrutura são válidos.

 `dwThreadId`\
 A ID do thread.

 `dwSuspendCount`\
 Contagem de suspensões do thread.

 `dwThreadState`\
 Um valor a partir de [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) enumeração que indica o estado do thread operacional.

 `bstrPriority`\
 Uma cadeia de caracteres que especifica a prioridade de thread; Por exemplo, "Acima do Normal", "Normal" ou "Tempo crítico".

 `bstName`\
 O nome do thread.

 `bstrLocation`\
 O local de thread (normalmente, o quadro de pilha mais alto), geralmente expressado como o nome do método em que a execução é interrompida no momento.

## <a name="remarks"></a>Comentários
 Essa estrutura é preenchida por uma chamada para o [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método. As informações retornadas então normalmente são usadas no preenchimento de **Threads** janela.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)