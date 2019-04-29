---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835509048e888e13b91c53d9e35bd03d7aebdfed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913495"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Especificado que tipo de informações para recuperar para um processo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="members"></a>Membros
 PIF_FILE_NAME Initialize/usar o `bstrFileName` campo do [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estrutura.

 PIF_BASE_NAME Initialize/usar o `bstrBaseName` campo do `PROCESS_INFO` estrutura.

 PIF_TITLE Initialize/usar o `bstrTitle` campo do `PROCESS_INFO` estrutura.

 PIF_PROCESS_ID Initialize/usar o `ProcessId` campo do `PROCESS_INFO` estrutura.

 PIF_SESSION_ID Initialize/usar o `dwSessionId` campo do `PROCESS_INFO` estrutura.

 PIF_ATTACHED_SESSION_NAME Initialize/usar o `bstrAttachedSessionName` campo do `PROCESS_INFO` estrutura.

 PIF_CREATION_TIME Initialize/usar o `CreationTime` campo do `PROCESS_INFO` estrutura.

 PIF_FLAGS Initialize/usar o `Flags` campo do `PROCESS_INFO` estrutura.

 PIF_ALL preenche todos os campos.

## <a name="remarks"></a>Comentários
 Passado para o [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) método para indicar quais campos da [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) são de estrutura a ser inicializado.

 Também é usado na `Fields` campo do `PROCESS_INFO` estrutura para indicar quais campos são usados e válido.

 Esses sinalizadores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)