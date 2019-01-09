---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 40c527881c45a935344aa5444d7397ccdb6d99e4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092489"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Notifica o objeto de criador de perfil que o mecanismo de script será executada uma chamada de função do modelo de objeto de documento (DOM).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwszFunctionName`  
 [in] O nome da função que o mecanismo de script será executada.  
  
 `scriptType`  
 [in] O tipo da função. Para obter descrições dos valores válidos, consulte [enumeração PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de retorno desse método é ignorado pelo mecanismo de script.  
  
## <a name="remarks"></a>Comentários  
 Para chamadas de DOM, o mecanismo de script chama esse método em vez de chamar [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Isso é devido ao grande número de métodos exclusivos e propriedades no DOM.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)