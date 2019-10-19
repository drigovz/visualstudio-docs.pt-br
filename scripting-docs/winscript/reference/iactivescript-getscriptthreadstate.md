---
title: 'IActiveScript:: GetScriptThreadState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578005"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Recupera o estado atual de um thread de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stidThread`  
 no Identificador do thread para o qual o estado é desejado ou um dos seguintes identificadores de thread especiais:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|O thread base; ou seja, o thread no qual o mecanismo de script foi instanciado.|  
|SCRIPTTHREADID_CURRENT|O thread atualmente em execução.|  
  
 `pstsState`  
 fora Endereço de uma variável que recebe o estado do thread indicado. O estado é indicado por um dos valores constantes nomeados definidos pela enumeração de [Enumeração SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) . Se esse parâmetro não identificar o thread atual, o estado poderá ser alterado a qualquer momento.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="remarks"></a>Comentários  
 Esse método pode ser chamado de threads não base sem resultar em um texto explicativo não base para hospedar objetos ou para a interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)