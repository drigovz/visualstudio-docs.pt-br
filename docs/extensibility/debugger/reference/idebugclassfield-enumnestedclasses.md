---
title: IDebugClassField::EnumNestedClasses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf46b0a143b61be6897caa0adb03ab40c375e7bb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206866"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Cria um enumerador para as classes aninhadas nessa classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`ppEnum`\
[out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de classes aninhadas. Retorna um valor nulo se não houver nenhuma classe aninhada.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhuma classe aninhada. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
Cada elemento da enumeração é um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que descreve uma classe aninhada.

Uma classe aninhada é uma classe definida dentro de outra classe. Por exemplo:

```
class RootClass {
   class NestedClass { }
};
```

O [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumeração conteria um objeto que representa o `NestedClass` classe.

## <a name="see-also"></a>Consulte também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
