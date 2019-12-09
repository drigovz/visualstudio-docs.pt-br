---
title: CONSTRUCTOR_ENUM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea240cf33bab70f1488a2aa90fecd71220b1da25
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346447"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
Seleciona os diferentes tipos de construtores.

## <a name="syntax"></a>Sintaxe

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="fields"></a>Campos
`crAll`\
Seleciona todos os construtores.

`crNonStatic`\
Seleciona os construtores não-estático.

`crStatic`\
Seleciona os construtores estáticos.

## <a name="remarks"></a>Comentários
Passado como um argumento para o [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) método.

## <a name="requirements"></a>Requisitos
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
