---
title: IDebugReference2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81398c79289786d2c63fa6f37725c295b690d905
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327545"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Compara uma referência a outro. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Parâmetros
`dwCompare`\
[in] Um valor a partir de [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) enumeração que especifica a operação de comparação, por exemplo, maior que ou igual a, menor que.

`pReference`\
[in] Uma [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa a referência a serem comparadas.

## <a name="return-value"></a>Valor de retorno
 Sempre retorna `E_NOTIMPL`.

## <a name="see-also"></a>Consulte também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)