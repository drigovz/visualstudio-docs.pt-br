---
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd481883c826ff21a82b52bdd82de087b6219b58
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309009"
---
# <a name="fieldkindex"></a>FIELD_KIND_EX
Enumera os tipos de campos adicionais que um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto pode conter. Esta enumeração estende o [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) enumeração.

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
Campo não contém um tipo estendido.

`FIELD_TYPE_EX_METHODVAR`\
Campo contém uma variável do método.

`FIELD_TYPE_EX_CLASSVAR`\
Campo contém uma variável de classe.

## <a name="requirements"></a>Requisitos
Cabeçalho: Sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
