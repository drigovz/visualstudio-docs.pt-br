---
title: IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs
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
ms.openlocfilehash: a198667e7dc30969c32b556620b139d52f833543
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993229"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifica o criador de perfil de um script compilado do objeto que o script do mecanismo. Esse método é chamado para cada script que é compilado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scriptId`  
 [in] A ID exclusiva do script que foi compilado. Essa ID é atribuída pelo mecanismo de script.  
  
 `type`  
 [in] O tipo de script que foi compilado. Os valores são definidos no [enumeração PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Se estiver disponível, um ponteiro para um `IUnknown` interface que o criador de perfis deve consultar um [IDebugDocumentContext Interface](../../winscript/reference/idebugdocumentcontext-interface.md) ponteiro. Caso contrário, será nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script pode fornecer o contexto do documento somente se isso for suportado pelo host.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)