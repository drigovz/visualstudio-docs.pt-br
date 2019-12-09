---
title: IDebugMethodField::GetGlobalContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77f3d82beab43b227dd3beb772dd41353d89b6fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324185"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Obtém o contêiner global do método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parâmetros
`ppClass`\
[out] Retorna um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa o módulo no qual esse método é definido.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Retornado [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto representa o módulo de inteiro e é um objeto artificial, ou seja, o próprio módulo não tem uma classe real, mas ele pode ser representado por um `IDebugClassField` objeto, permitindo que os vários elementos do módulo a ser enumerado e descobertos.

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)