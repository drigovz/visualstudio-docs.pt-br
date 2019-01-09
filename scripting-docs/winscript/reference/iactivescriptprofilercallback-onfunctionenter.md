---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 887810d12a20045c95b0f837db1592b9b7bf301e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095375"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Notifica o objeto de criador de perfil que o mecanismo de script está prestes a executar uma chamada de função não é uma chamada no modelo de objeto de documento (DOM).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnFunctionEnter(  
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
 Para chamadas de DOM, o mecanismo de script chama [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) em vez de `IActiveScriptProfilerCallback::OnFunctionEnter`. Isso é devido ao grande número de métodos exclusivos e propriedades no DOM.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)