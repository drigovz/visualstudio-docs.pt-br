---
title: BP_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02550141fb1857214d5bfd80d5dd86969bec9fba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737793"
---
# <a name="bp_type"></a>BP_TYPE
Especifica se o ponto de ruptura está em um local de código, é um local de dados ou é outro tipo de ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Campos
`BPT_NONE`\
Não especifica nenhum tipo de ponto de ruptura.

`BPT_CODE`\
Especifica um ponto de quebra de código.

`BPT_DATA`\
Especifica um ponto de ruptura de dados.

`BPT_SPECIAL`\
Especifica um ponto de ruptura que não é nem um código nem um tipo de dados. Este tipo é preterido e não deve ser usado.

## <a name="remarks"></a>Comentários
Passou como parâmetro para os métodos [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) e [GetBreakpointType.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
