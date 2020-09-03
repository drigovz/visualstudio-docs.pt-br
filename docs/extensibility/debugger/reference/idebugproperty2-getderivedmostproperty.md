---
title: 'IDebugProperty2:: GetDerivedMostProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721497"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Obtém a propriedade mais derivada de uma propriedade.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Parâmetros
`ppDerivedMost`\
fora Retorna um objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa a propriedade mais derivada.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro. Retorna `S_GETDERIVEDMOST_NO_DERIVED_MOST` se não houver nenhuma propriedade derivada para recuperar.

## <a name="remarks"></a>Comentários
 Por exemplo, se essa propriedade descrever um objeto que implementa, `ClassRoot` mas que, na verdade, é uma instanciação de `ClassDerived` que é derivada de `ClassRoot` , esse método retornará um objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que descreve o `ClassDerived` objeto.

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
