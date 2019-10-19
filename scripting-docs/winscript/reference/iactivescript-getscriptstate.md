---
title: 'IActiveScript:: getscriptstate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575731"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Recupera o estado atual do mecanismo de script. Esse método pode ser chamado de threads não base sem resultar em um texto explicativo não base para hospedar objetos ou para a interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pss`  
 fora Endereço de uma variável que recebe um valor definido na enumeração de [Enumeração scriptstate](../../winscript/reference/scriptstate-enumeration.md) . O valor indica o estado atual do mecanismo de script associado ao thread de chamada.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se for bem-sucedido ou `E_POINTER` se um ponteiro inválido tiver sido especificado.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)