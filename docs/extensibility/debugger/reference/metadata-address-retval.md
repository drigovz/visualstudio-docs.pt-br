---
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714269"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Esta estrutura representa um valor de retorno de um método ou função.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Membros
 `tokMethod`\
 O ID do método para o valor deste retorno é para.

 `dwCorType`\
 O tipo base de valor de retorno. Este é um `CorElementType` valor da enumeração definida no arquivo .NET Framework SDK corhdr.h.

 `dwSigSize`\
 O tamanho da assinatura do valor `rgSig`de retorno (como armazenado em ).

 `rgSig`\
 Uma matriz de bytes formando a assinatura do valor de retorno.

## <a name="remarks"></a>Comentários
 Essa estrutura faz parte da união na [estrutura DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando o `dwKind` campo da `DEBUG_ADDRESS_UNION` estrutura é definido para `ADDRESS_KIND_RETVAL` (um valor da enumeração [ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
