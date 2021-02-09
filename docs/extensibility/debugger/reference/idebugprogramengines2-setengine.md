---
title: 'IDebugProgramEngines2:: setengine | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ecdf136e40dc4227b8f6378409cb7fe43f6659d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898883"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Informa ao programa ou nó de programa qual mecanismo DE depuração (DE) usar para depurar este programa.

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

## <a name="parameters"></a>Parâmetros
`guidEngine`\
no O GUID do de.

## <a name="return-value"></a>Valor de retorno
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
