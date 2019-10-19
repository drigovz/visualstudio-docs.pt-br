---
title: 'IActiveScriptSite:: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570207"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informa ao host que o script concluiu a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvarResult`  
 no Endereço de uma variável que contém o resultado do script ou `NULL` se o script não produziu nenhum resultado.  
  
 `pexcepinfo`  
 no Endereço de uma estrutura de `EXCEPINFO` que contém informações de exceção geradas quando o script foi encerrado ou `NULL` se nenhuma exceção foi gerada.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se houver êxito.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script chama esse método antes da chamada para o método [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) , com o sinalizador SCRIPTSTATE_INITIALIZED definido, é concluído. Esse método pode ser usado para retornar o status de conclusão e os resultados para o host. Observe que muitas linguagens de script, que se baseiam em eventos de coletor do host, têm estendes que são definidas pelo host. Nesse caso, esse método nunca pode ser chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)