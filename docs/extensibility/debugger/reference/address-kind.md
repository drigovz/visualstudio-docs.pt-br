---
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738155"
---
# <a name="address_kind"></a>ADDRESS_KIND
Especifica os tipos de endereços.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Campos
`ADDRESS_KIND_NATIVE`\
Um endereço nativo, representado pela estrutura [NATIVE_ADDRESS.](../../../extensibility/debugger/reference/native-address.md)

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Um endereço não gerenciado `this` em`Me` relação a um ponteiro (no Visual Basic) e representado pela estrutura [UNMANAGED_ADDRESS_THIS_RELATIVE.](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Um endereço físico não gerenciado, representado pela estrutura [UNMANAGED_ADDRESS_PHYSICAL.](../../../extensibility/debugger/reference/unmanaged-address-physical.md)

`ADDRESS_KIND_METHOD`\
Um método de classe, representado pela estrutura [METADATA_ADDRESS_METHOD.](../../../extensibility/debugger/reference/metadata-address-method.md)

`ADDRESS_KIND_FIELD`\
Um campo de uma classe, representado pela estrutura [METADATA_ADDRESS_FIELD.](../../../extensibility/debugger/reference/metadata-address-field.md)

`ADDRESS_KIND_LOCAL`\
O endereço é para uma variável local e é representado pela estrutura [METADATA_ADDRESS_LOCAL.](../../../extensibility/debugger/reference/metadata-address-local.md)

`ADDRESS_KIND_PARAM`\
Um parâmetro de método ou função, representado pela estrutura [METADATA_ADDRESS_PARAM.](../../../extensibility/debugger/reference/metadata-address-param.md)

`ADDRESS_KIND_ARRAYELEM`\
Um elemento de matriz, representado pela estrutura [METADATA_ADDRESS_ARRAYELEM.](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)

`ADDRESS_KIND_RETVAL`\
Um valor de retorno, representado pela estrutura [METADATA_ADDRESS_RETVAL.](../../../extensibility/debugger/reference/metadata-address-retval.md)

## <a name="remarks"></a>Comentários
O método [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) retorna a estrutura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) que contém uma união de possíveis estruturas, a [estrutura DEBUG_ADDRESS_UNION.](../../../extensibility/debugger/reference/debug-address-union.md) O `dwKind` campo `DEBUG_ADDRESS_UNION` da estrutura `ADDRESS_KIND` detém o valor e descreve como interpretar o campo sindical.

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
