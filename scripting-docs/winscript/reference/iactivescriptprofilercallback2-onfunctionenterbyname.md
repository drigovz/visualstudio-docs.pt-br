---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571631"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Notifica o objeto Profiler que o mecanismo de script vai executar uma chamada de função Modelo de Objeto do Documento (DOM).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwszFunctionName`  
 no O nome da função que o mecanismo de script vai executar.  
  
 `scriptType`  
 no O tipo da função. Para obter descrições de valores válidos, consulte [PROFILER_SCRIPT_TYPE Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valor retornado  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 Para chamadas DOM, o mecanismo de script chama esse método em vez de chamar [IActiveScriptProfilerCallback:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Isso ocorre devido ao grande número de métodos e propriedades exclusivos no DOM.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)