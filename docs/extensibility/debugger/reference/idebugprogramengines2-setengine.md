---
title: IDebugProgramEngines2:SetEngine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 226f5bbf11627a3171641806a673eaa15b614572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722410"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Informa ao programa ou nó de programa que depurar o motor (DE) para usar para depurar este programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>parâmetros
`guidEngine`\
[em] O GUID do DE.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
