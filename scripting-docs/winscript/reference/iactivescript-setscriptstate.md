---
title: 'IActiveScript:: setscriptstate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577996"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Coloca o mecanismo de script no estado fornecido. Esse método pode ser chamado de threads não base sem resultar em um texto explicativo não base para hospedar objetos ou para a interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ss`  
 no Define o mecanismo de script para o estado fornecido. Pode ser um dos valores definidos na enumeração de [Enumeração scriptstate](../../winscript/reference/scriptstate-enumeration.md) .  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_FAIL`|O mecanismo de script não dá suporte à transição de volta para o estado inicializado. O host deve descartar esse mecanismo de script e criar, inicializar e carregar um novo mecanismo de script para obter o mesmo efeito.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado) e, portanto, falhou.|  
|`OLESCRIPT_S_PENDING`|O método foi enfileirado com êxito, mas o estado ainda não foi alterado. Quando o estado for alterado, o site será chamado de volta pelo método [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|O método foi bem-sucedido, mas o script já estava no estado especificado.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre os Estados do mecanismo de script, consulte a seção Estados do mecanismo de script dos [mecanismos de script do Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)    
 [IActiveScript:: GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)    
 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)    
 [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)