---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738194"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Especifica como interpretar um ID de processo na estrutura [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

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
ID de processo é um identificador de sistema. Use `ProcessId.dwProcessId` o campo da estrutura [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

`AD_PROCESS_ID_GUID`\
O ID do processo é um GUID. Use `ProcessId.guidProcessId` o campo `AD_PROCESS_ID` da estrutura.

## <a name="remarks"></a>Comentários
Utilizado para `ProcessIdType` o membro da [estrutura AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) identificar o tipo de ID do processo que está contido na estrutura. Determina como interpretar `ProcessId` a união na estrutura.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
