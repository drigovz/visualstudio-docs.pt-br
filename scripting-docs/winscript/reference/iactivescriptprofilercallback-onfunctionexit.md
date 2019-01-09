---
title: IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fb3f71e9a8a383e2362bacb17698f4eec58f464e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092191"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Notifica o criador de perfil de objeto que o mecanismo de script terminar de executar uma função chamada que não é uma chamada no modelo de objeto de documento (DOM).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scriptId`  
 [in] A ID exclusiva do que a função faz parte do script. Essa ID é atribuída pelo mecanismo de script.  
  
 `functionId`  
 [in] A ID exclusiva da função. Essa ID é atribuída pelo mecanismo de script.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 Para chamadas de DOM, o mecanismo de script chama [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) em vez de `IActiveScriptProfilerCallback::OnFunctionExit`. Isso é devido ao grande número de métodos exclusivos e propriedades no DOM.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)