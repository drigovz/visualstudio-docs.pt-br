---
title: THREADPROPERTIES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713433"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Descreve as propriedades de um fio.

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
 Uma combinação de bandeiras da [enumeração THREADPROPERTY_FIELDS,](../../../extensibility/debugger/reference/threadproperty-fields.md) descrevendo quais campos nesta estrutura são válidos.

 `dwThreadId`\
 A im.

 `dwSuspendCount`\
 A contagem de suspensão de linha.

 `dwThreadState`\
 Um valor da enumeração [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) indicando o estado do segmento operacional.

 `bstrPriority`\
 Uma seqüência especificando a prioridade de segmento; por exemplo, "Acima do Normal", "Normal" ou "Time Critical".

 `bstName`\
 O nome da linha.

 `bstrLocation`\
 O local de rosca (geralmente o quadro de pilha superior), normalmente expresso como o nome do método onde a execução é atualmente interrompida.

## <a name="remarks"></a>Comentários
 Essa estrutura é preenchida por uma chamada para o método [GetThreadProperties.](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) As informações tão retornadas são normalmente usadas na preencher a janela **Threads.**

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
