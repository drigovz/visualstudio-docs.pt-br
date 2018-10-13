---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68e6344e356b085b16311a5d685b019acbd87b70
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297694"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna os GUIDs para todos os possíveis depuração mecanismos (DES) que podem depurá-lo.  
  
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
 [in] O número de GUIDs DE retornar. Isso também especifica o tamanho máximo da `rgguidEngines` matriz.  
  
 `rgguidEngines`  
 [no, out] Uma matriz DE GUIDs a serem preenchidos.  
  
 `pceltEngines`  
 [out] Retorna o número real de GUIDs DE que são retornados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna o [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou [c#] 0x8007007A se o buffer não for grande o suficiente.  
  
## <a name="remarks"></a>Comentários  
 Para determinar quantos mecanismos lá são, chame esse método uma vez com o `celtBuffer` parâmetro definido como 0 e o `rgguidEngines` parâmetro definido como um valor nulo. Isso retorna `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A para c#) e o `pceltEngines` parâmetro retorna o tamanho necessário do buffer.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)

