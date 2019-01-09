---
title: IActiveScriptSite::OnStateChange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee4fd06b00c674c9c50ce253186aeee3165bac66
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097403"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
Informa ao host que o mecanismo de script foi alterado de estados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ssScriptState`  
 [in] Valor que indica o novo estado de script. Consulte a [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) método para obter uma descrição dos Estados.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se houver êxito.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)