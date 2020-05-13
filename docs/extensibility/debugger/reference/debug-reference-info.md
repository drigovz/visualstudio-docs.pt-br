---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737408"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Descreve uma referência.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Membros
`dwFields`\
Uma combinação de bandeiras da enumeração [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) que especifica quais campos são preenchidos.

`bstrName`\
O nome especificado pelo usuário do objeto [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

`bstrType`\
O tipo de referência como uma seqüência formatada.

`bstrValue`\
O valor de referência como uma seqüência formatada

`dwAttrib`\
Uma combinação de bandeiras da enumeração [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que especifica as bandeiras para os atributos de propriedade depuração.

`dwRefType`\
Um valor da enumeração [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) que especifica se o tipo de referência é forte ou fraco.

`m_pReference`\
Um objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que especifica as informações de referência.

## <a name="remarks"></a>Comentários
Essa estrutura é passada para uma chamada para o método [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) a ser preenchida. Essa estrutura também é devolvida como parte de uma lista da interface [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) que, por sua vez, é devolvida de uma chamada para o método [EnumChildren.](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
