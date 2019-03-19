---
title: IActiveScript::Close | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53b71471ada55751de301391fdcc70387c1bb6c2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157043"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Faz com que o mecanismo de script abandonar a qualquer script carregado no momento, perder seu estado e liberar quaisquer ponteiros de interface, que ele tem a outros objetos, portanto, inserindo um estado fechado. Coletores de eventos, o texto do script executado imediatamente e chamadas de macro que já estão em andamento são concluídas antes das alterações de estado (use [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) para cancelar um thread em execução do script). Esse método deve ser chamado pelo host criando antes que a interface seja liberada para evitar problemas de referência circular.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`S_OK`|Êxito.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script já estava no estado fechado).|  
|`OLESCRIPT_S_PENDING`|O método foi enfileirado com êxito, mas o estado ainda não foi alterado. Quando as alterações de estado, o site é ser o retorno de chamada a [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) método.|  
|`S_FALSE`|O método foi bem-sucedido, mas o script já foi fechado.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)