---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352e4bdf6c79dc67f0bf396cb1164e96e80fbf5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337695"
---
# <a name="fieldinfo"></a>FIELD_INFO
Essa estrutura descreve uma variável local, parâmetro ou outro campo.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Membros
`dwFields`\
Uma combinação de sinalizadores do [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumeração que especifica quais membros são preenchidos.

`bstrFullName`\
O nome completo do campo.

`bstrName`\
O nome curto do campo.

`bstrType`\
O tipo do campo.

`dwModifiers`\
Uma combinação de sinalizadores do [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumeração que descreve o campo.

## <a name="remarks"></a>Comentários
Essa estrutura é passada para o [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método onde ele é preenchido.

## <a name="requirements"></a>Requisitos
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
