---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 488c2b1a96d01e0e7dfa9868d2f7e5111adc4e2d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699425"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Especifica as informações a serem recuperados sobre uma falha na resolução de um ponto de interrupção.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="members"></a>Membros
PERESI_BPRESLOCATION Initialize/usar o `bpResLocation` campo (localização de resolução de ponto de interrupção) a [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estrutura.

BPERESI_PROGRAM Initialize/usar o `pProgram` campo do `BP_ERROR_RESOLUTION_INFO` estrutura.

BPERESI_THREAD Initialize/usar o `pThread` campo do `BP_ERROR_RESOLUTION_INFO` estrutura.

BPERESI_MESSAGE Initialize/usar o `bstrMessage` campo do `BP_ERROR_RESOLUTION_INFO` estrutura.

BPERESI_TYPE Initialize/usar o `dwType` campo (tipo de ponto de interrupção) da `BP_ERROR_RESOLUTION_INFO` estrutura.

BPERESI_ALLFIELDS Initialize/usar todos os campos do `BP_ERROR_RESOLUTION_INFO` estrutura.

## <a name="remarks"></a>Comentários
Passado como um parâmetro para o [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método para indicar quais campos da [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) são de estrutura a ser inicializado.

Esses valores também são usados para indicar quais campos no `BP_ERROR_RESOLUTION_INFO` estrutura são usados e válidos quando essa estrutura é retornada.

Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
