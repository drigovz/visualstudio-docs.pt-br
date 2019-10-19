---
title: 'IActiveScriptProfilerControl:: StopProfiling | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StopProfiling
apilocation:
- scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5900678093d57b3c995ac3bca8464ccd612fb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571545"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Interrompe a criação de perfil no mecanismo de script. Esse método chama [IActiveScriptProfilerCallback:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) no objeto Profiler e, em seguida, libera-o.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hrShutdownReason`  
 no O HRESULT a ser passado como um parâmetro para o método [IActiveScriptProfilerCallback:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) do objeto Profiler.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|A criação de perfil não está habilitada.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)