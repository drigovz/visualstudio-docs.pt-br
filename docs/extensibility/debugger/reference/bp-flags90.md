---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738051"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Enumera valores válidos para bandeiras opcionais. Os sinalizadores opcionais podem ser usados para especificar informações adicionais quando você definir um ponto de ruptura. Essa enumeração estende a [enumeração BP_FLAGS.](../../../extensibility/debugger/reference/bp-flags.md)

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Campos
`BP90_FLAG_NONE`\
Não especifica nenhum sinalizador de ponto de ruptura.

`BP90_FLAG_MAP_DOCPOSITION`\
Especifica que o mecanismo de depuração (DE) deve mapear o ponto de ruptura usando a posição do documento. Isso é aplicável apenas aos pontos de interrupção definidos em arquivos de origem orientados a script, como ASP (Active Server Pages, páginas de servidor ativo).

`BP90_FLAG_DONT_STOP`\
Especifica que o ponto de partida deve ser processado pelo motor de depuração, mas que o motor de depuração não deve parar por aí; ou seja, um objeto de evento [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) não deve ser enviado. Esta bandeira foi projetada para ser usada principalmente com pontos de rastreamento.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Usado pelo motor de depuração nativo para determinar se o estado de desestatador deve ser limpo. Ele difere de BP90_FLAG_DONT_STOP porque BP90_FLAG_DONT_STOP não é definido se o ponto de rastreamento executa uma macro.

## <a name="requirements"></a>Requisitos
Cabeçalho: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
