---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01465a0b921d61a07c4d31c8d4d4ba4b70e5bafd
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206853"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Cria um enumerador para os enumeradores aninhados dessa classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`ppEnum`\
[out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de enumerações aninhadas. Retorna um valor nulo se não houver nenhum enumerações aninhadas.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum enumeradores aninhados. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
Cada elemento da enumeração é um [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que descreve uma enumeração aninhada.

Uma enumeração declarada dentro de uma classe é considerada uma enumeração aninhada. Por exemplo, com base em:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

O `EnumNestedEnums` método retornaria um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que contém um objeto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que representa o `NestedEnum` enumeração.

## <a name="see-also"></a>Consulte também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
