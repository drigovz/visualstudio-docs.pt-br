---
title: IActiveScriptSite::OnScriptTerminate | Microsoft Docs
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
ms.openlocfilehash: 664f974b26a2cae0d1e16d37dc3bc66e95993d6f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144817"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informa ao host que o script tiver concluído a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvarResult`  
 [in] Endereço de uma variável que contém o resultado do script, ou `NULL` se o script não produziu nenhum resultado.  
  
 `pexcepinfo`  
 [in] Endereço de um `EXCEPINFO` estrutura que contém informações de exceção geradas quando o script é encerrado, ou `NULL` se nenhuma exceção foi gerada.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se houver êxito.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script chama esse método antes de chamar o [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) método com o sinalizador SCRIPTSTATE_INITIALIZED definido, é concluído. Esse método pode ser usado para retornar o status de conclusão e os resultados para o host. Observe que muitas linguagens de script, que são baseadas em eventos de coletor do host, têm períodos de vida que são definidos pelo host. Nesse caso, esse método nunca pode ser chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)