---
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81fa3cf9504c4b883a075999fa1993ea0e8e8529
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315723"
---
# <a name="bpflags"></a>BP_FLAGS
Fornece sinalizadores opcionais que podem ser usados para especificar informações adicionais ao definir um ponto de interrupção.

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

## <a name="members"></a>Membros
BP_FLAG_NONE  
Não especifica que nenhum sinalizador de ponto de interrupção.

BP_FLAG_MAP_DOCPOSITION  
Especifica que o mecanismo de depuração (DES) deve mapear o ponto de interrupção usando a posição do documento. Isso é aplicável somente a pontos de interrupção definidos em arquivos de origem e orientada a script, como Active Server Pages (ASP).

BP_FLAG_DONT_STOP  
Especifica que o ponto de interrupção deve ser processado pelo mecanismo de depuração, mas que o mecanismo de depuração, por fim, não deve parar existe (ou seja, uma [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) objeto de evento não deve ser enviado). Esse sinalizador é projetado para ser usado principalmente com tracepoints.

## <a name="remarks"></a>Comentários
Usado para o `dwFlags` membro a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas.

Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
[Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
