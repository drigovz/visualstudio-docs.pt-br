---
title: IDebugObject2::GetAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d08d9108ed4a433bcbcb17d6d4587532542b303
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872457"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Obtém o alias associado com esse objeto, se houver.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

#### <a name="parameters"></a>Parâmetros
 `ppAlias`

 [out] Retorna um [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) objeto que representa o alias para esse objeto; caso contrário, retornará um valor nulo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Um alias para um objeto é criado com uma chamada para o [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)