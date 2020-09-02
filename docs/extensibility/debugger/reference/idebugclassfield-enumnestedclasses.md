---
title: 'IDebugClassField:: EnumNestedClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734435"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Cria um enumerador para as classes aninhadas nesta classe.

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
fora Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa a lista de classes aninhadas. Retorna um valor nulo se não houver nenhuma classe aninhada.

## <a name="return-value"></a>Valor Retornado
Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver classes aninhadas. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
Cada elemento da enumeração é um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que descreve uma classe aninhada.

Uma classe aninhada é uma classe definida dentro de outra classe. Por exemplo:

```
class RootClass {
   class NestedClass { }
};
```

A enumeração [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) conterá um objeto que representa a `NestedClass` classe.

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
