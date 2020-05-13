---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722438"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Retorna os GUIDs para todos os possíveis motores de depuração (DE) que podem depurar este programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>parâmetros
`celtBuffer`\
[em] O número de DE GUIDs para retornar. Isso também especifica o tamanho `rgguidEngines` máximo da matriz.

`rgguidEngines`\
[dentro, fora] Uma matriz de DE GUIDs a serem preenchidos.

`pceltEngines`\
[fora] Retorna o número real de DE GUIDs que são devolvidos.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Retorna [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [C#] 0x8007007A se o buffer não for grande o suficiente.

## <a name="remarks"></a>Comentários
 Para determinar quantos motores existem, chame este `celtBuffer` método uma vez `rgguidEngines` com o parâmetro definido como 0 e o parâmetro definido como um valor nulo. Isso `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` retorna (0x8007007A para C#), e o `pceltEngines` parâmetro retorna o tamanho necessário do buffer.

## <a name="see-also"></a>Confira também
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
