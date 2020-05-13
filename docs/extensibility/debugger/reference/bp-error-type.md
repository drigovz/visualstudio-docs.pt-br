---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738069"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Especifica o tipo de erro de um ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Campos
`BPET_NONE`\
Não especifica nenhum erro de ponto de ruptura.

`BPET_TYPE_WARNING`\
Especifica um erro de ponto de quebra no estilo de aviso.

`BPET_TYPE_ERROR`\
Especifica um erro de ponto de quebra no estilo de erro.

`BPET_SEV_HIGH`\
Especifica um erro de ponto de ruptura de alta gravidade.

`BPET_SEV_GENERAL`\
Especifica um erro de ponto de ruptura de gravidade média.

`BPET_SEV_LOW`\
Especifica um erro de ponto de ruptura de baixa gravidade.

`BPET_TYPE_MASK`\
Especifica um erro de ponto de ruptura no estilo da máscara.

`BPET_SEV_MASK`\
Especifica um erro de ponto de ruptura no estilo severidade da máscara.

`BPET_GENERAL_WARNING`\
Especifica um erro de ponto de quebra no estilo de aviso geral.

`BPET_GENERAL_ERROR`\
Especifica um erro de ponto de quebra no estilo de erro geral.

`BPET_ALL`\
Especifica todos os tipos de erro de ponto de ruptura.

## <a name="remarks"></a>Comentários
Esses valores podem ser combinados com um pouco e utilizados `OR` para o `dwType` membro da estrutura [BP_ERROR_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Passou como parâmetro para o método [EnumErrorBreakpoints.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

Um tipo de erro de ponto de ruptura é composto de um tipo e uma gravidade. Isso significa que um tipo de erro de ponto `BPET_TYPE_ERROR`de ruptura nunca é apenas `BPET_SEV_GENERAL`um tipo (por exemplo, ,) ou uma gravidade (por exemplo, ) por si só. `BPET_GENERAL_WARNING`e `BPET_GENERAL_ERROR` fornecer valores predefinidos para pontos de interrupção de advertência e erro gerais.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
