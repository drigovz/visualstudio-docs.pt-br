---
title: 'IActiveScriptProfilerCallback2:: OnFunctionExitByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571623"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifica o objeto Profiler de que o mecanismo de script concluiu a execução de uma chamada de função Modelo de Objeto do Documento (DOM).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwszFunctionName`  
 no O nome da função que o mecanismo de script concluiu a execução.  
  
 `scriptType`  
 no O tipo da função. Para obter descrições de valores válidos, consulte [Enumeração PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valor retornado  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 Para chamadas DOM, o mecanismo de script chama esse método em vez de chamar [IActiveScriptProfilerCallback:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Isso ocorre devido ao grande número de métodos e propriedades exclusivos no DOM.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerCallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)