---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef0844e4bf2c10128ee9c1a62669711e36eb401f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682434"
---
# <a name="bpflags90"></a>BP_FLAGS90
Enumera os valores válidos para sinalizadores opcionais. Os sinalizadores opcionais podem ser usados para especificar informações adicionais quando você definir um ponto de interrupção. Esta enumeração estende o [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumeração.

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

#### <a name="parameters"></a>Parâmetros
BP90_FLAG_NONE não especifica nenhum sinalizador de ponto de interrupção.

BP90_FLAG_MAP_DOCPOSITION Especifica que o mecanismo de depuração (DES) deve mapear o ponto de interrupção usando a posição do documento. Isso é aplicável somente a pontos de interrupção definidos em arquivos de origem e orientada a script, como Active Server Pages (ASP).

BP90_FLAG_DONT_STOP Especifica que o ponto de interrupção deve ser processado pelo mecanismo de depuração, mas que o mecanismo de depuração, por fim, não deve parar lá; ou seja, uma [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) objeto de evento não deve ser enviado. Esse sinalizador é projetado para ser usado principalmente com os pontos de rastreamento.

BP90_FLAG_TRACEPOINT_CONTINUE usado pelo mecanismo de depuração nativa para determinar se o estado de execução em etapas deve ser apagado. Ele difere de BP90_FLAG_DONT_STOP porque BP90_FLAG_DONT_STOP não será definido se o ponto de rastreamento executa uma macro.

## <a name="requirements"></a>Requisitos
Cabeçalho: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
