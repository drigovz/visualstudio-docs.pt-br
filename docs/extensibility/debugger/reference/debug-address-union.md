---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737533"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Descreve diferentes tipos de endereços.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Membros
`dwKind`\
Um valor da [enumeração ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) especificando como interpretar a união.

`addr.addrNative`\
[Somente C++] Contém [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) a estrutura `dwKind` NATIVE_ADDRESS if = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Somente C++] Contém[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) a estrutura `dwKind` UNMANAGED_ADDRESS_THIS_RELATIVE if = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Somente C++] Contém[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) a estrutura `dwKind` UNMANAGED_ADDRESS_PHYSICAL if = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Somente C++] Contém[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) a estrutura `dwKind` METADATA_ADDRESS_METHOD if = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Somente C++] Contém[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) a estrutura `dwKind` METADATA_ADDRESS_FIELD se = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Somente C++] Contém[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) a estrutura `dwKind` METADATA_ADDRESS_LOCAL se = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Somente C++] Contém[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) a estrutura `dwKind` METADATA_ADDRESS_PARAM if = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Somente C++] Contém[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) a estrutura `dwKind` METADATA_ADDRESS_ARRAYELEM if = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Somente C++] Contém[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) a estrutura `dwKind` METADATA_ADDRESS_RETVAL se = ADDRESS_KIND_RETVAL.

`addr.unused`\
[C++ somente] preenchimento.

`addr`\
[Somente C++] O nome do sindicato.

`unionmember`\
[C# apenas] Esse valor precisa ser reparado para `dwKind`o tipo de estrutura adequada com base em . Veja observações para `dwKind` a associação entre e interpretação do sindicato.

## <a name="remarks"></a>Comentários
Essa estrutura faz parte da estrutura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) e representa um dos `DEBUG_ADDRESS` vários tipos de endereços diferentes (a estrutura é preenchida por uma chamada para o método [GetAddress).](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)

 [C# apenas] A tabela a seguir `unionmember` mostra como interpretar o membro para cada tipo de endereço. O Exemplo mostra como isso é feito para um tipo de endereço.

|`dwKind`|`unionmember`interpretado como|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Exemplo
Este exemplo mostra como interpretar um`METADATA_ADDRESS_ARRAYELEM`tipo `DEBUG_ADDRESS_UNION` de endereço ( ) da estrutura em C#. Os elementos restantes podem ser interpretados exatamente da mesma maneira.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
