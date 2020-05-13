---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737515"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Esta estrutura representa um endereço.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Membros
`ulAppDomainID`\
A id do processo.

`guidModule`\
O GUID do módulo que contém este endereço.

`tokClass`\
O token que identifica a classe ou o tipo deste endereço.

> [!NOTE]
> Este valor é específico para um provedor de símbolos e, portanto, não tem nenhum significado geral além de um identificador para um tipo de classe.

`addr`\
Uma [estrutura DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) que contém uma união de estruturas que descrevem os tipos de endereços individuais. O `addr`valor.`dwKind` vem da [enumeração ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) que explica como interpretar a união.

## <a name="remarks"></a>Comentários
Esta estrutura é passada para o método [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) a ser preenchido.

**Aviso [Somente C++]**

Se `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` é `addr.addr.addrLocal.pLocal` e se não for um `Release` valor nulo, então você deve chamar o ponteiro de token:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
