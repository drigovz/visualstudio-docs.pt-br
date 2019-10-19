---
title: 'IActiveScriptProfilerCallback:: OnFunctionExit | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571676"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Notifica o objeto Profiler de que o mecanismo de script concluiu a execução de uma chamada de função que não é uma chamada para o Modelo de Objeto do Documento (DOM).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scriptId`  
 no A ID exclusiva do script do qual a função faz parte. Essa ID é atribuída pelo mecanismo de script.  
  
 `functionId`  
 no A ID exclusiva da função. Essa ID é atribuída pelo mecanismo de script.  
  
## <a name="return-value"></a>Valor retornado  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 Para chamadas DOM, o mecanismo de script chama [IActiveScriptProfilerCallback2:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) em vez de `IActiveScriptProfilerCallback::OnFunctionExit`. Isso ocorre devido ao grande número de métodos e propriedades exclusivos no DOM.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerCallback:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)