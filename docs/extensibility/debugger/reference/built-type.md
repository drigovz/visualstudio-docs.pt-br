---
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737701"
---
# <a name="built_type"></a>BUILT_TYPE
Esta estrutura especifica informações sobre um tipo de campo extraído de metadados.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Membros
`ulAppDomainID`\
ID do aplicativo de onde veio o símbolo. Isso é usado para identificar exclusivamente uma instância do aplicativo.

`guidModule`\
O GUID do módulo que contém este campo.

`pUnderlyingField`\
Um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) identificando o campo subjacente associado a este campo construído.

## <a name="remarks"></a>Comentários
Essa estrutura aparece como parte da união `dwKind` na estrutura `TYPE_INFO` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando `TYPE_KIND_BUILT` o campo da estrutura é definido para (um valor da [enumeração dwTYPE_KIND).](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
