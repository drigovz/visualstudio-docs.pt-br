---
title: 'IEnumDebugFields:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5725d16577b9d22d280b17cc572b7335cd2331ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896921"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Esse método retorna o número de elementos na enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parâmetros
`pcelt`\
fora Retorna o número de elementos na enumeração.

## <a name="return-value"></a>Valor de retorno
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método não faz parte da interface de enumeração COM personalizada que especifica que somente avançar, clonar, ignorar e redefinir precisam ser implementados.

## <a name="see-also"></a>Confira também
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
