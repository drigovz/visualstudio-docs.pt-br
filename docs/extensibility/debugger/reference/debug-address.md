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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e02f78e82c87bceb10b71bcb303a78f25a9a623e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899118"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Essa estrutura representa um endereço.

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
A ID do processo.

`guidModule`\
O GUID do módulo que contém esse endereço.

`tokClass`\
O token que identifica a classe ou o tipo deste endereço.

> [!NOTE]
> Esse valor é específico para um provedor de símbolos e, portanto, não tem um significado geral diferente de como um identificador para um tipo de classe.

`addr`\
Uma estrutura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , que contém uma União de estruturas que descreve os tipos de endereço individuais. O valor `addr` .`dwKind` vem da enumeração de [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , que explica como interpretar a União.

## <a name="remarks"></a>Comentários
Essa estrutura é passada para o método [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) a ser preenchido.

**Aviso [somente C++]**

Se `addr.dwKind` for `ADDRESS_KIND_METADATA_LOCAL` e se `addr.addr.addrLocal.pLocal` não for um valor nulo, você deverá chamar `Release` no ponteiro do token:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requisitos
Cabeçalho: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
