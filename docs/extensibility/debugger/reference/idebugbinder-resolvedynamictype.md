---
title: IDebugBinder::ResolveDynamicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveDynamicType
helpviewer_keywords:
- IDebugBinder::ResolveDynamicType method
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3e490d06444d555625136d6b7ba2a8e99169f59
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735982"
---
# <a name="idebugbinderresolvedynamictype"></a>IDebugBinder::ResolveDynamicType
Este método retorna o tipo exato de uma variável.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ResolveDynamicType (
   IDebugDynamicField *pDynamic,
   IDebugField       **ppResolved
);
```

```csharp
int ResolveDynamicType(
   IDebugDynamicField pDynamic,
   out IDebugField    ppResolved
);
```

## <a name="parameters"></a>parâmetros
`pDynamic`\
[em] Um [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) representando um tipo de variável.

`ppResolved`\
[fora] Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) dando informações específicas sobre o tipo da variável.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)
