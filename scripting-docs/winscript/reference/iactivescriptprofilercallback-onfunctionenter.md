---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571693"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Notifica o objeto Profiler que o mecanismo de script está prestes a executar uma chamada de função que não é uma chamada para o Modelo de Objeto do Documento (DOM).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnFunctionEnter(  
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
 Para chamadas DOM, o mecanismo de script chama [IActiveScriptProfilerCallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) em vez de `IActiveScriptProfilerCallback::OnFunctionEnter`. Isso ocorre devido ao grande número de métodos e propriedades exclusivos no DOM.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)