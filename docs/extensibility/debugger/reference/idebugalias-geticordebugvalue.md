---
title: 'IDebugAlias:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba5456ba3beabb1d5418d739be2aa74838daa41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947171"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera uma interface de código gerenciado que representa o valor associado a esse alias.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parâmetros
`ppUnk`\
[fora] `IUnknown` interface que representa o valor associado a este alias. Essa interface pode ser consultada para a `ICorDebugValue` interface.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método se aplica somente a valores gerenciados (o `ICorDebugValue` é uma interface disponível no .NET Framework e é definido no SDK do .NET Framework no arquivo CorDebug. idl).

## <a name="see-also"></a>Consulte também
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
