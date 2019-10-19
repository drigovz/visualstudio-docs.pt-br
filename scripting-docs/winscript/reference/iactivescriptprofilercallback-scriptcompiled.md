---
title: 'IActiveScriptProfilerCallback:: ScriptCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571667"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifica o objeto Profiler de que o mecanismo de script compilou um script. Esse método é chamado para cada script que é compilado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scriptId`  
 no A ID exclusiva do script que foi compilado. Essa ID é atribuída pelo mecanismo de script.  
  
 `type`  
 no O tipo do script que foi compilado. Os valores são definidos na [Enumeração PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 no Se disponível, um ponteiro para uma interface `IUnknown` que o criador de perfil deve consultar para um ponteiro de [interface IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) . Caso contrário, isso será nulo.  
  
## <a name="return-value"></a>Valor retornado  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script pode fornecer o contexto do documento somente se ele tiver suporte no host.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)