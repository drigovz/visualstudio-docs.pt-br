---
title: IDebugArrayField::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736301"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Obtém a classificação ou número de dimensões da matriz.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>parâmetros
`pdwRank`\
[fora] Devolve a patente.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A classificação de uma matriz corresponde ao número de dimensões. Em C++ e C#, matrizes multidimensionais são realmente matrizes de matrizes e, `GetRank` portanto, podem ser consideradas apenas uma matriz unidimensional (e o método sempre retorna 1). Em [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], por outro lado, matrizes multidimensionais são tratadas de forma diferente e a `GetRank` classificação de tal matriz reflete o número de dimensões (e o método sempre retorna o número de dimensões).

## <a name="see-also"></a>Confira também
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
