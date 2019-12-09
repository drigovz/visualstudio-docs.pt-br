---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8775087b9ec212f7e7d7e1547d01a5f175c4dc22
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329819"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Obtém a referência do mais derivado de uma referência. Reservado para uso futuro.

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

## <a name="parameters"></a>Parâmetros
`ppDerivedMost`\
[out] Retorna um [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa a propriedade mais derivado.

## <a name="return-value"></a>Valor de retorno
 Sempre retorna `E_NOTIMPL`.

## <a name="remarks"></a>Comentários
 Por exemplo, se esta propriedade descreve um objeto que implementa `ClassRoot` , mas o que é realmente uma instanciação de `ClassDerived` que é derivada de `ClassRoot`, em seguida, esse método retorna um [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa uma referência para o `ClassDerived` objeto.

## <a name="see-also"></a>Consulte também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)