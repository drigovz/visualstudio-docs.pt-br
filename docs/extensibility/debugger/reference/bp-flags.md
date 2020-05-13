---
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738065"
---
# <a name="bp_flags"></a>BP_FLAGS
Fornece sinalizadores opcionais que podem ser usados para especificar informações adicionais ao definir um ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Campos
`BP_FLAG_NONE`\
Não especifica nenhum sinalizador de ponto de ruptura.

`BP_FLAG_MAP_DOCPOSITION`\
Especifica que o mecanismo de depuração (DE) deve mapear o ponto de ruptura usando a posição do documento. Isso é aplicável apenas aos pontos de interrupção definidos em arquivos de origem orientados a script, como ASP (Active Server Pages, páginas de servidor ativo).

`BP_FLAG_DONT_STOP`\
Especifica que o ponto de partida deve ser processado pelo mecanismo de depuração, mas que o motor de depuração não deve parar por aí (ou seja, um objeto de evento [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) não deve ser enviado). Esta bandeira foi projetada para ser usada principalmente com pontos de rastreamento.

## <a name="remarks"></a>Comentários
Usado para `dwFlags` o membro das estruturas [de BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
