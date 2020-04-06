---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737236"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Especifica os critérios para comparar dois contextos de documentos.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Campos
`DOCCONTEXT_EQUAL`\
Encontre o primeiro contexto de documento na lista que seja igual ao contexto do documento-alvo.

`DOCCONTEXT_LESS_THAN`\
Encontre o primeiro contexto de documento na lista que seja menor que o contexto do documento-alvo.

`DOCCONTEXT_GREATER_THAN`\
Encontre o primeiro contexto de documento na lista que é maior do que o contexto do documento-alvo.

`DOCCONTEXT_SAME_DOCUMENT`\
Encontre o primeiro contexto de documento na lista que está no mesmo documento do contexto do documento-alvo.

## <a name="remarks"></a>Comentários
Passou como um argumento para o método [Compare.](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

Esses valores são usados para especificar um critério de comparação para encontrar o primeiro contexto do documento em uma lista. Um contexto de documento recebe uma lista de contextos documentais para se comparar através do `IDebugDocumentContext2::Compare` método. O primeiro contexto de documento na lista `true` para a qual o operador de comparação é então devolvido.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
