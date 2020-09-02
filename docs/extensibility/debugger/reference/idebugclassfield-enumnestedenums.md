---
title: 'IDebugClassField:: EnumNestedEnums | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734414"
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
fora Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa a lista de enumerações aninhadas. Retorna um valor nulo se não houver nenhuma Enumeração aninhada.

## <a name="return-value"></a>Valor Retornado
Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver enumeradores aninhados. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
Cada elemento da enumeração é um objeto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) que descreve uma enumeração aninhada.

Uma enumeração declarada dentro de uma classe é considerada uma enumeração aninhada. Por exemplo, considerando que:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

O `EnumNestedEnums` método retornaria um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que contém um objeto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) que representa a `NestedEnum` enumeração.

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
