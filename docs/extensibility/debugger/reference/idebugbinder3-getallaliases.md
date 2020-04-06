---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735812"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Este método recupera uma lista de codinomes do programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>parâmetros
`uRequest`\
[em] O número máximo de aliases a retornar (especifica `ppAliases`o comprimento da matriz passada para ).

`ppAliases`\
[dentro, fora] Matriz para preencher com pseudônimos (se este `uRequest` for um valor nulo e for 0, a contagem de pseudônimos que podem ser devolvidos será devolvida por `puFetched`).

`puFetched`\
[fora] Retorna o número de codinomes obtidos.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
