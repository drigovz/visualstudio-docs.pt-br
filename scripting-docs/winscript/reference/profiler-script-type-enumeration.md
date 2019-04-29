---
title: Enumeração PROFILER_SCRIPT_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca90a566db422d75fefc44267ffe10504bb872ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816779"
---
# <a name="profilerscripttype-enumeration"></a>Enumeração PROFILER_SCRIPT_TYPE
Especifica o tipo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Especifica o código de script escrito pelo usuário.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Especifica o código de script que é gerado dinamicamente durante a execução.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Especifica o tipo de script para funções nativas e objetos que são definidos pelo mecanismo de script.|  
|PROFILER_SCRIPT_TYPE_DOM|Especifica uma chamada para o modelo DOM (Document Object) do Internet Explorer, por exemplo, uma chamada para o `document.getElementById` método.|  
  
## <a name="see-also"></a>Consulte também  
 [Script ativo Profiler constantes, enumerações e estruturas](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)