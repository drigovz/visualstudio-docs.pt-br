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
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574578"
---
# <a name="profiler_script_type-enumeration"></a>Enumeração PROFILER_SCRIPT_TYPE
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
|PROFILER_SCRIPT_TYPE_DYNAMIC|Especifica o código de script gerado dinamicamente durante a execução.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Especifica o tipo de script para funções nativas e objetos que são definidos pelo mecanismo de script.|  
|PROFILER_SCRIPT_TYPE_DOM|Especifica uma chamada para o Modelo de Objeto do Documento (DOM) do Internet Explorer, por exemplo, uma chamada para o método `document.getElementById`.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [IActiveScriptProfilerCallback:: ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)    
 [IActiveScriptProfilerCallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)