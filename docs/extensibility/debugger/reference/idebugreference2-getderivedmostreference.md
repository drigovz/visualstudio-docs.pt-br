---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15e98884d040cfb2ebf1b33a56c7edea331fbff0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720620"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Obtém a referência mais derivada de uma referência. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>parâmetros
`ppDerivedMost`\
[fora] Retorna um objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa a propriedade derivada.

## <a name="return-value"></a>Valor retornado
 Retorna sempre `E_NOTIMPL`.

## <a name="remarks"></a>Comentários
 Por exemplo, se esta propriedade descreve `ClassRoot` um objeto que implementa, `ClassDerived` mas que `ClassRoot`na verdade é uma instanciação disso é derivado, então esse método retorna um objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) representando uma referência ao `ClassDerived` objeto.

## <a name="see-also"></a>Confira também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
