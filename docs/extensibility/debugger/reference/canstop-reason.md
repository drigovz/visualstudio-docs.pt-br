---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbc4143c61a0223fe3940b4167748727d1ebd560
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711612"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Usado para determinar se um programa pode interromper a execução depois de atingir um ponto específico na execução.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="members"></a>Membros
CANSTOP_ENTRYPOINT Especifica o ponto de entrada de um determinado programa.

CANSTOP_STEPIN Especifica entrar em uma função.

## <a name="remarks"></a>Comentários
Passado como um argumento para o [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para confirmar com a sessão de depuração SDM (Gerenciador de), se ele for okey parar depois de atingir o ponto de entrada do programa, ou depois de passar para uma função ou método.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
