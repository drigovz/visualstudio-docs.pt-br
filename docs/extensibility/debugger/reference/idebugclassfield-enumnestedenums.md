---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734414"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Cria um enumerador para os enumeradores aninhados desta classe.

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

## <a name="parameters"></a>parâmetros
`ppEnum`\
[fora] Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) representando a lista de enumerações aninhadas. Retorna um valor nulo se não houver enumerações aninhadas.

## <a name="return-value"></a>Valor retornado
Se for bem-sucedido, retorna S_OK ou retorna S_FALSE se não houver enumeradores aninhados. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
Cada elemento da enumeração é um objeto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) descrevendo uma enumeração aninhada.

Uma enumeração declarada dentro de uma classe é considerada uma enumeração aninhada. Por exemplo, considerando que:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

O `EnumNestedEnums` método retornaria um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que contém um objeto `NestedEnum` [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) que representa a enumeração.

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
