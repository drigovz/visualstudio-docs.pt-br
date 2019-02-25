---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9dc3185b644a1045428ead9f2c9851916df3249c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698229"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Retorna os GUIDs para todos os possíveis depuração mecanismos (DES) que podem depurá-lo.

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

#### <a name="parameters"></a>Parâmetros
 `celtBuffer`

 [in] O número de GUIDs DE retornar. Isso também especifica o tamanho máximo da `rgguidEngines` matriz.

 `rgguidEngines`

 [no, out] Uma matriz DE GUIDs a serem preenchidos.

 `pceltEngines`

 [out] Retorna o número real de GUIDs DE que são retornados.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna o [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [C#] 0x8007007A se o buffer não for grande o suficiente.

## <a name="remarks"></a>Comentários
 Para determinar quantos mecanismos lá são, chame esse método uma vez com o `celtBuffer` parâmetro definido como 0 e o `rgguidEngines` parâmetro definido como um valor nulo. Isso retorna `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A para c#) e o `pceltEngines` parâmetro retorna o tamanho necessário do buffer.

## <a name="see-also"></a>Consulte também
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)