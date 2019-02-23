---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a18d9a158e69fd18319f187274a2db7d00e24546
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720621"
---
# <a name="processinfo"></a>PROCESS_INFO
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
 Campos de uma combinação de sinalizadores do [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) enumeração que especificam quais campos são preenchidos.

 o nome de caminho completo do processo de bstrFileName. Equivalente a chamar o [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) método com o parâmetro `GN_FILENAME`.

 bstrBaseName o nome do arquivo e extensão do processo. Equivalente a chamar o `IDebugProcess2::Getname` método com o parâmetro `GN_BASENAME`.

 bstrTitle o título do processo, se houver. Equivalente a chamar o `IDebugProcess2::Getname` método com o parâmetro `GN_TITLE`.

 ProcessId a [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura que identifica o processo. Equivalente a chamar o [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) método.

 dwSessionId o identificador da sessão de depuração que esse processo está em execução no.

 bstrAttachedSessionName o nome da sessão anexado. Equivalente a chamar o [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) método.

 CreationTime a hora em que o processo foi criado.

 Sinaliza uma combinação de sinalizadores do [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) enumeração que especificam propriedades do processo.

## <a name="remarks"></a>Comentários
 Essa estrutura é passada para o [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) método onde ele é preenchido.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)