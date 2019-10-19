---
title: 'IActiveScript:: fechar | Microsoft Docs'
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
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575788"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Faz com que o mecanismo de script abandone qualquer script carregado atualmente, perca seu estado e libere qualquer ponteiro de interface que tenha para outros objetos, inserindo assim um estado fechado. Coletores de eventos, executados imediatamente em texto de script e invocações de macro que já estão em andamento são concluídos antes das alterações de estado (use [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) para cancelar um thread de script em execução). Esse método deve ser chamado pelo host de criação antes que a interface seja liberada para evitar problemas de referência circular.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`S_OK`|Êxito.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script já estava no estado Closed).|  
|`OLESCRIPT_S_PENDING`|O método foi enfileirado com êxito, mas o estado ainda não foi alterado. Quando o estado for alterado, o site será chamado de volta no método [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|O método foi bem-sucedido, mas o script já foi fechado.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)