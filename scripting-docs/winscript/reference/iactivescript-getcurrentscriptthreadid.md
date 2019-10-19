---
title: 'IActiveScript:: GetCurrentScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575773"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Recupera um identificador definido pelo mecanismo de script para o thread em execução no momento. O identificador pode ser usado em chamadas subsequentes para métodos de controle de execução de thread de script, como o método [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstidThread`  
 fora Endereço de uma variável que recebe o identificador de thread de script associado ao thread atual. A interpretação desse identificador é deixada para o mecanismo de script, mas pode ser apenas uma cópia do identificador de thread do Windows. Se o Thread Win32 for encerrado, esse identificador se tornará não atribuído e poderá ser atribuído posteriormente a outro thread.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se for bem-sucedido ou `E_POINTER` se um ponteiro inválido tiver sido especificado.  
  
## <a name="remarks"></a>Comentários  
 Esse método pode ser chamado de threads não base sem resultar em um texto explicativo não base para hospedar objetos ou para a interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)