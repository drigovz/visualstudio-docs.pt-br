---
title: 'IDebugAlias:: GetObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ff5459903b5259d6005a4ebb01228117c2801db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944778"
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Obtém o objeto para o qual este alias se destina.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetObject(
   IDebugObject2** ppObject
);
```

```csharp
int GetObject(
   Out IDebugObject2 ppObject
)
```

## <a name="parameters"></a>Parâmetros
`ppObject`\
fora O [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) que este alias representa.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
