---
title: IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4bd032914605c61b13a0a56a42e510c2af252f7e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091397"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifica o criador de perfil de objeto do mecanismo de script encontrou uma função ao compilar um script.  
  
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
 [in] A ID exclusiva da função. Essa ID é atribuída pelo mecanismo de script.  
  
 `scriptId`  
 [in] A ID exclusiva do que a função faz parte do script.  
  
 `pwszFunctionName`  
 [in] O nome da função, ou null para uma função anônima.  
  
 `pwszFunctionNameHint`  
 [in] O nome deduzido da função, ou nulo se o mecanismo de script não deduz qualquer nome.  
  
 `pIDebugDocumentContext`  
 [in] Se estiver disponível, o ponteiro para um `IUnknown` interface que o criador de perfis deve consultar um [IDebugDocumentContext Interface](../../winscript/reference/idebugdocumentcontext-interface.md) ponteiro. Caso contrário, nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script pode fornecer o contexto do documento somente se isso for suportado pelo host.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)