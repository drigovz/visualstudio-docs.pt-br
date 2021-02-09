---
title: 'IDebugReference2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6cebc34bdd1515ad632a0165fcdc900999b383fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909739"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Compara uma referência a outra. Reservado para uso futuro.

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
no Um valor da enumeração [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) que especifica a operação de comparação, por exemplo, igual a, menor que ou maior que.

`pReference`\
no Um objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa a referência a ser comparado com.

## <a name="return-value"></a>Valor retornado
 Sempre retorna `E_NOTIMPL`.

## <a name="see-also"></a>Confira também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
