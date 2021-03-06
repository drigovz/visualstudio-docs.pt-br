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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d01485a6044122baf460eede90470c5cc1478323
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912996"
---
# <a name="bp_type"></a>BP_TYPE
Especifica se o ponto de interrupção está em um local de código, é um local de dados ou outro tipo de ponto de interrupção.

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
Especifica nenhum tipo de ponto de interrupção.

`BPT_CODE`\
Especifica um ponto de interrupção de código.

`BPT_DATA`\
Especifica um ponto de interrupção de dados.

`BPT_SPECIAL`\
Especifica um ponto de interrupção que não é um código nem um tipo de dados. Esse tipo é preterido e não deve ser usado.

## <a name="remarks"></a>Comentários
Passado como um parâmetro para os métodos [Getbreakpointtype](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) e [getbreakpointtype](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
