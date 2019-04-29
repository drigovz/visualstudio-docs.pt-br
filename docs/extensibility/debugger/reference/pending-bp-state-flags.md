---
title: PENDING_BP_STATE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7614b0633f6490e8c3bb6837ed89fda67575c71e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913697"
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
Especifica os sinalizadores de estado do ponto de interrupção pendente.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
typedef DWORD PENDING_BP_STATE_FLAGS;
```

```csharp
public enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
```

## <a name="members"></a>Membros
 Espaço reservado PBPSF_NONE.

 PBPSF_VIRTUALIZED Especifica um virtualizado pendente do ponto de interrupção, que deve ser associado sempre que o novo código é carregado.

## <a name="remarks"></a>Comentários
 Usado para o `flags` membro a [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) estrutura.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)