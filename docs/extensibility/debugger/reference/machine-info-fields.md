---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714511"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Especifica que tipo de informação recuperar para uma determinada máquina.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Campos
 `MCIF_NAME`\
 Inicializar/usar `bstrName` o campo na estrutura.

 `MCIF_FLAGS`\
 Inicializar/usar `Flags` o campo na estrutura.

 `MIF_ALL`\
 Inicializar/utilizar todos os campos da estrutura.

## <a name="remarks"></a>Comentários
 Esses valores são passados para o método [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) para indicar quais membros da estrutura [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) devem ser inicializados.

 Também utilizado `Fields` no membro `MACHINE_INFO` da estrutura para indicar quais campos são usados e válidos.

 Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
