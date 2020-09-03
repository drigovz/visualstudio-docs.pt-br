---
title: 'IDebugProgramEngines2:: EnumPossibleEngines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182180"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna os GUIDs para todos os mecanismos de depuração possíveis que podem depurar este programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 no O número de DE GUIDs a serem retornados. Isso também especifica o tamanho máximo da `rgguidEngines` matriz.  
  
 `rgguidEngines`  
 [entrada, saída] Uma matriz de DE GUIDs a ser preenchida.  
  
 `pceltEngines`  
 fora Retorna o número real de GUIDs que são retornados.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [C#] 0x8007007A se o buffer não for grande o suficiente.  
  
## <a name="remarks"></a>Comentários  
 Para determinar quantos mecanismos existem, chame esse método uma vez com o `celtBuffer` parâmetro definido como 0 e o `rgguidEngines` parâmetro definido como um valor nulo. Isso retorna `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A para C#) e o `pceltEngines` parâmetro retorna o tamanho necessário do buffer.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
