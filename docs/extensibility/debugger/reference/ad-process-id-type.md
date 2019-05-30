---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9df097037a84af9da63f0a98ee6cfa3b28cfcdd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351384"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Especifica como interpretar uma ID de processo na [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Campos
`AD_PROCESS_ID_SYSTEM`\
ID do processo é um identificador de sistema. Use o `ProcessId.dwProcessId` campo do [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura.

`AD_PROCESS_ID_GUID`\
ID do processo é um GUID. Use o `ProcessId.guidProcessId` campo do `AD_PROCESS_ID` estrutura.

## <a name="remarks"></a>Comentários
Usado para o `ProcessIdType` membro do [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura para identificar o tipo de ID do processo que está contido na estrutura. Determina como interpretar o `ProcessId` union na estrutura.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
