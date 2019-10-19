---
title: 'IActiveScriptProfilerCallback:: FunctionCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576468"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifica o objeto Profiler que o mecanismo de script encontrou uma função ao compilar um script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID exclusiva da função. Essa ID é atribuída pelo mecanismo de script.  
  
 `scriptId`  
 no A ID exclusiva do script do qual a função faz parte.  
  
 `pwszFunctionName`  
 no O nome da função ou nulo para uma função anônima.  
  
 `pwszFunctionNameHint`  
 no O nome inferido da função, ou NULL se o mecanismo de script não inferir nenhum nome.  
  
 `pIDebugDocumentContext`  
 no Se disponível, o ponteiro para uma interface `IUnknown` que o criador de perfil deve consultar para um ponteiro de [interface IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) . Caso contrário, NULL.  
  
## <a name="return-value"></a>Valor retornado  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script pode fornecer o contexto do documento somente se ele tiver suporte no host.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)