---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737923"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Especifica a condição associada à contagem de passes de ponto de ruptura que faz com que o ponto de ruptura seja acionado.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Campos
`BP_PASSCOUNT_NONE`\
Não especifica nenhum estilo de contagem de passes de ponto de ruptura.

`BP_PASSCOUNT_EQUAL`\
Define o estilo de contagem de passes de ponto de quebra igual. O ponto de partida dispara quando o número de vezes que o ponto de partida é atingido é igual à contagem de passes.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Define o estilo de contagem de passes de ponto de ruptura igual ou maior. O ponto de partida dispara quando o número de vezes que o ponto de ruptura é atingido é igual ou maior do que a contagem de passes.

`BP_PASSCOUNT_MOD`\
Especifica uma contagem de passes de módulo. Por exemplo, se a contagem `BP_PASSCOUNT_MOD` de passes for do tipo e o valor da contagem de passes for 4, o ponto de partida é acionado toda vez que a contagem de acertos for um múltiplo de 4.

## <a name="remarks"></a>Comentários
Usado para `stylePassCount` o membro da estrutura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que, por sua vez, é membro das estruturas [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
