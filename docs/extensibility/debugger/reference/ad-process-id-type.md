---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c600dd1fcf22ac7e32e91a38c98d6f524a9ba79
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315645"
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

## <a name="members"></a>Membros
ID do processo AD_PROCESS_ID_SYSTEM é um identificador de sistema. Use o `ProcessId.dwProcessId` campo do [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura.

ID do processo AD_PROCESS_ID_GUID é um GUID. Use o `ProcessId.guidProcessId` campo do `AD_PROCESS_ID` estrutura.

## <a name="remarks"></a>Comentários
Usado para o `ProcessIdType` membro do [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura para identificar o tipo de ID do processo que está contido na estrutura. Determina como interpretar o `ProcessId` union na estrutura.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
[Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
