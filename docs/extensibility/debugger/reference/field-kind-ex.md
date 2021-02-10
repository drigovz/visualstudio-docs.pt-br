---
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3742e60c1bc8a0e490ca83ba14eadc4b879d3e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936893"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Enumera tipos adicionais de campos que um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pode conter. Essa enumeração estende a enumeração de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) .

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>Campos
`FIELD_KIND_EX_NONE`\
O campo não contém um tipo estendido.

`FIELD_TYPE_EX_METHODVAR`\
O campo contém uma variável de método.

`FIELD_TYPE_EX_CLASSVAR`\
O campo contém uma variável de classe.

## <a name="requirements"></a>Requisitos
Cabeçalho: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
