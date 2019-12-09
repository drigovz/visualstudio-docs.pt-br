---
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6707c09e409e2a04d7afec0322b575a70cea33cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349867"
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Especifica o estado de um ponto de interrupção pendente (um ponto de interrupção que ainda não foi associado).

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Campos
 `PBPS_NONE`\
 Espaço reservado para zero. Esse valor nunca é retornado.

 `PBPS_DELETED`\
 Indica que o ponto de interrupção pendente foi excluído.

 `PBPS_DISABLED`\
 Indica que o ponto de interrupção pendente está desabilitado.

 `PBPS_ENABLED`\
 Indica que o ponto de interrupção pendente está habilitado.

## <a name="remarks"></a>Comentários
 Usar como o `state` membro a [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) estrutura.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)