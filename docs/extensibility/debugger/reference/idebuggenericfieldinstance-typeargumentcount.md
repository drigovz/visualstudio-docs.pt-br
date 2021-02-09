---
title: 'IDebugGenericFieldInstance:: TypeArgumentCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b811780bf135a700f0ea451ef148598fe621e4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928348"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Retorna o número de argumentos de parâmetro de tipo para esta instância.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Parâmetros
`pcArgs`\
[entrada, saída] Número de argumentos de parâmetro de tipo para esta instância.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Por exemplo, se List \<int> , esse método retornará 1 e, se List, \<int,float2> esse método retornará 2. Esse método retornará 0 se não houver nenhum argumento de tipo.

## <a name="see-also"></a>Confira também
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
