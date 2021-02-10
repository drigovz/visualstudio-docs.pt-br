---
title: 'IDebugArrayField:: GetNumberOfElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3454624feab268af089a5e82e38c0cce3d23ab03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940300"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Obtém o número de elementos na matriz.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

## <a name="parameters"></a>Parâmetros
`pdwNumElements`\
fora Retorna o número de elementos na matriz.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O valor retornado é o número total de elementos na matriz, independentemente do número de dimensões.

## <a name="see-also"></a>Confira também
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
