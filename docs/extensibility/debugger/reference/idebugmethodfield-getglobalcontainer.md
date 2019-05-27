---
title: IDebugMethodField::GetGlobalContainer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcd816b74e5c1474e89ab5b9550df8787c8210ee
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211950"
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