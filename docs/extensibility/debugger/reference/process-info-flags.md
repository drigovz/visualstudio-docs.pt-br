---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713959"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Descreve ou especifica propriedades de um processo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Campos

`PIFLAG_SYSTEM_PROCESS`\
Indica que o processo é um processo de sistema.

`PIFLAG_DEBUGGER_ATTACHED`\
Indica que o processo está sendo depurado por um depurador. Pode ser [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] um depurador, ou pode ser algum outro depurador, por exemplo, o WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica que o processo está parado. Válido somente `PIFLAG_DEBUGGER_ATTACHED` se também for especificado. Disponível no Visual Studio 2005 e posterior.

`PIFLAG_PROCESS_RUNNING`\
Indica que o processo está em andamento. Válido somente `PIFLAG_DEBUGGER_ATTACHED` se também for especificado. Disponível no Visual Studio 2005 e posterior.

## <a name="remarks"></a>Comentários

Usado para `Flags` o membro da estrutura [PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos

Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também

- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
