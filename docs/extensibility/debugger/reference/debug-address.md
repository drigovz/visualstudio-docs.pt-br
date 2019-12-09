---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc25fb53db918486029e931a06a9e2de37f81c5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346306"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
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
A ID de processo.

`guidModule`\
O GUID do módulo que contém esse endereço.

`tokClass`\
O token de identificação de classe ou tipo desse endereço.

> [!NOTE]
> Esse valor é específico para um provedor de símbolo e, portanto, não tem nenhum significado geral diferente de como um identificador para um tipo de classe.

`addr`\
Um [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura, que contém uma união de estruturas que descrevem os tipos de endereço individual. O valor `addr`.`dwKind` é proveniente de [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração, que explica como interpretar a união.

## <a name="remarks"></a>Comentários
Essa estrutura é passada para o [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método a ser preenchido.

**Aviso [C++ somente]**

Se `addr.dwKind` está `ADDRESS_KIND_METADATA_LOCAL` e, se `addr.addr.addrLocal.pLocal` não é um valor nulo, em seguida, você deve chamar `Release` no ponteiro de token:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requisitos
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
