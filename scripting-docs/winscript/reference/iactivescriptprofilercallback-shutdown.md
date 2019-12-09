---
title: 'IActiveScriptProfilerCallback:: Shutdown | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571652"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Chamado para informar o objeto Profiler sempre que a criação de perfil for interrompida em um mecanismo de script. Dessa forma, o objeto Profiler pode chamar suas rotinas de limpeza, se necessário. Esse método também é chamado pelo mecanismo de script quando o mecanismo de script está sendo desligado ou quando uma chamada para [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) falha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hrReason`  
 no O motivo para desligar. Se o mecanismo de script estiver sendo desligado, `S_OK` será passado. Se a chamada para [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) retornar um HRESULT de falha, o HRESULT será passado. Caso contrário, esse valor será recuperado de [IActiveScriptProfilerControl:: StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valor retornado  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)