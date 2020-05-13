---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713880"
---
# <a name="process_info"></a>PROCESS_INFO
Contém informações sobre um processo.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Membros
 `Fields`\
 Uma combinação de bandeiras da enumeração [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) que especificam quais campos são preenchidos.

 `bstrFileName`\
 O nome completo do caminho do processo. Equivalente a chamar o método [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) com o parâmetro `GN_FILENAME`.

 `bstrBaseName`\
 O nome do arquivo e a extensão do processo. Equivalente a `IDebugProcess2::Getname` chamar o método `GN_BASENAME`com o parâmetro .

 `bstrTitle`\
 O título do processo, se existir. Equivalente a `IDebugProcess2::Getname` chamar o método `GN_TITLE`com o parâmetro .

 `ProcessId`\
 A [estrutura AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que identifica o processo. Equivalente a chamar o método [GetPhysicalProcessId.](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

 `dwSessionId`\
 O identificador da sessão de depuração em que este processo está sendo executado.

 `bstrAttachedSessionName`\
 O nome da sessão anexada. Equivalente a chamar o método [GetAttachedSessionName.](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

 `CreationTime`\
 O tempo que o processo foi criado.

 `Flags`\
 Uma combinação de bandeiras da [enumeração PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) que especificam propriedades do processo.

## <a name="remarks"></a>Comentários
 Essa estrutura é passada para o método [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) onde é preenchida.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
