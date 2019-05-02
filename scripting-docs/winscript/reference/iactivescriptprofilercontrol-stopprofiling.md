---
title: IActiveScriptProfilerControl::StopProfiling | Microsoft Docs
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
ms.openlocfilehash: 750693db9aa809e6b3521f0312cebcf45d8d720d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993002"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Interrompe a criação de perfil no mecanismo de script. Este método chama [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) no objeto do criador de perfil e o libera.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hrShutdownReason`  
 [in] O HRESULT a ser passado como um parâmetro para o [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) método do objeto criador de perfil.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Criação de perfil não está habilitada.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)