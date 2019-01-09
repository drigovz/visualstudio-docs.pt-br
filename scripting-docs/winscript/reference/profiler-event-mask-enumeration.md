---
title: Enumeração PROFILER_EVENT_MASK | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da55371c24f6a21acbc9dc789a2c76ef6e7c66b4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096662"
---
# <a name="profilereventmask-enumeration"></a>Enumeração PROFILER_EVENT_MASK
Indica os tipos de eventos que devem ser analisados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Funções de perfis que são definidas no script escrito pelo usuário e código dinâmico.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Funções nativas perfis definidos pelo mecanismo de script.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Perfis de todas as funções de mecanismo de script e definidas pelo usuário, excluindo chamadas no modelo de objeto de documento (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Funções de perfis que chamam o DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Perfis de todas as funções, incluindo as chamadas no DOM.|  
  
## <a name="see-also"></a>Consulte também  
 [Script ativo Profiler constantes, enumerações e estruturas](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)