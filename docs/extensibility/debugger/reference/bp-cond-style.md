---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738120"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Especifica o estilo de condição de ponto de interrupção para pontos de interrupção pendentes e vinculados.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Campos
`BP_COND_NONE`\
Dispara o ponto de ruptura quando a posição do ponto de ruptura é atingida. Nenhuma condição de ponto de ruptura especificada.

`BP_COND_WHEN_TRUE`\
Dispara o ponto de ruptura somente quando a expressão `true`condicional associada ao ponto de ruptura é avaliada em .

`BP_COND_WHEN_CHANGED`\
Dispara o ponto de ruptura somente quando o valor da expressão condicional associada ao ponto de ruptura mudou de sua avaliação anterior.

## <a name="remarks"></a>Comentários
Usado para `styleCondition` o membro da estrutura [BP_CONDITION.](../../../extensibility/debugger/reference/bp-condition.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
