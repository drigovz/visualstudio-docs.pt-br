---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736890"
---
# <a name="field_info"></a>FIELD_INFO
Esta estrutura descreve uma variável local, parâmetro ou outro campo.

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
Uma combinação de bandeiras da enumeração [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) que especifica quais membros estão preenchidos.

`bstrFullName`\
O nome completo do campo.

`bstrName`\
O nome curto do campo.

`bstrType`\
O tipo do campo.

`dwModifiers`\
Uma combinação de bandeiras da [enumeração FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) que descreve o campo.

## <a name="remarks"></a>Comentários
Essa estrutura é passada para o método [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) onde é preenchida.

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
