---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0694d83409a492a1d950a17ac5e2298ba9b8578
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309395"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Descreve ou especifica as propriedades de um processo.

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
Indica que o processo é um processo do sistema.

`PIFLAG_DEBUGGER_ATTACHED`\
Indica que o processo está sendo depurado por um depurador. Pode ser um [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador, ou ele pode ser de alguns outro depurador, por exemplo, o WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica que o processo é interrompido. Válido somente se `PIFLAG_DEBUGGER_ATTACHED` também for especificado. Disponível no Visual Studio 2005 e versões posteriores.

`PIFLAG_PROCESS_RUNNING`\
Indica que o processo está em execução. Válido somente se `PIFLAG_DEBUGGER_ATTACHED` também for especificado. Disponível no Visual Studio 2005 e versões posteriores.

## <a name="remarks"></a>Comentários

Usado para o `Flags` membro a [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estrutura.

Esses sinalizadores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos

Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também

- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)