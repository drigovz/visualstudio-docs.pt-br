---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
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
ms.openlocfilehash: a0066894830c111a8e0ad18f7acdc09d6114162e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935593"
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
 [in] Identificador do thread para o qual o estado for desejado, ou um dos seguintes identificadores de thread especial:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|O thread base. ou seja, o thread no qual o script do mecanismo foi instanciado.|  
|SCRIPTTHREADID_CURRENT|O thread em execução no momento.|  
  
 `pstsState`  
 [out] Endereço de uma variável que recebe o estado do thread indicado. O estado é indicado por um dos valores de constantes nomeados definidos pelo [enumeração SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) enumeração. Se esse parâmetro não identifica o thread atual, o estado pode ser alterado a qualquer momento.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="remarks"></a>Comentários  
 Esse método pode ser chamado de threads não base sem resultando em um balão não base para objetos de host ou o [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)