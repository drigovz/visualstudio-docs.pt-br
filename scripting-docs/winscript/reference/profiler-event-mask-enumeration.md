---
title: Enumeração PROFILER_EVENT_MASK | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c1e1e7f3b604832014cb23245b105756d1126c5b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572288"
---
# <a name="profiler_event_mask-enumeration"></a>Enumeração PROFILER_EVENT_MASK
Indica os tipos de eventos que devem ser cujo perfil deve ser criado.  
  
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
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Funções de perfis que são definidas no script gravado pelo usuário e código dinâmico.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Cria perfis de funções nativas que são definidas pelo mecanismo de script.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Cria perfis de todas as funções de mecanismo de script e definidas pelo usuário, excluindo chamadas para o Modelo de Objeto do Documento (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Funções de perfis que chamam o DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Cria perfis de todas as funções, incluindo chamadas para o DOM.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [IActiveScriptProfilerControl:: SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)    
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)