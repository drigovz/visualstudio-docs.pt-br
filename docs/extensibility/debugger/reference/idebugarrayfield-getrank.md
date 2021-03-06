---
title: 'IDebugArrayField:: getrank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10f42ca10496d89955032bd531651186d0aecf37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926348"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Obtém a classificação ou o número de dimensões da matriz.

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

## <a name="parameters"></a>Parâmetros
`pdwRank`\
fora Retorna a classificação.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A classificação de uma matriz corresponde ao número de dimensões. Em C++ e C#, matrizes multidimensionais são realmente matrizes de matrizes e, portanto, podem ser consideradas apenas uma matriz unidimensional (e o `GetRank` método sempre retorna 1). Em [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] , por outro lado, as matrizes multidimensionais são tratadas de forma diferente e a classificação de tal matriz reflete o número de dimensões (e o `GetRank` método sempre retorna o número de dimensões).

## <a name="see-also"></a>Confira também
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
