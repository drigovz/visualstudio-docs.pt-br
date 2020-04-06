---
title: IDebugReference2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d293fcb89c92a19acc4f5a3910015914ef4231a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720644"
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

## <a name="parameters"></a>parâmetros
`dwCompare`\
[em] Um valor da [enumeração REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) que especifica a operação de comparação, por exemplo, igual a, menor ou maior que.

`pReference`\
[em] Um objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) representando a referência a ser comparado.

## <a name="return-value"></a>Valor retornado
 Retorna sempre `E_NOTIMPL`.

## <a name="see-also"></a>Confira também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
