---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737778"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Dá a razão de um ponto de ruptura não ter sido vinculado.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>Campos
`BPUR_UNKNOWN`\
A razão é desconhecida.

`BPUR_CODE_UNLOADED`\
O código que contém o ponto de ruptura foi descarregado.

`BPUR_BREAKPOINT_REBIND`\
O ponto de ruptura foi a repercussão para um local diferente. Isso pode acontecer após editar e continuar as operações quando o ponto de ruptura se mover, ou quando o ponto de ruptura estiver vinculado a um arquivo com um caminho que não é mais válido.

`BPUR_ BREAKPOINT_ERROR`\
O ponto de ruptura é determinado para estar errado depois de ser vinculado. Isso acontece com pontos de interrupção gerenciados cujas condições não são mais válidas.

## <a name="remarks"></a>Comentários
Devolvido pelo método [GetReason.](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
