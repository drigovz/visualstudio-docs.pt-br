---
title: 'IActiveScript:: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577261"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrompe a execução de um thread de script em execução (um coletor de eventos, uma execução imediata ou uma chamada de macro). Esse método pode ser usado para encerrar um script que está preso (por exemplo, em um loop infinito). Ele pode ser chamado de threads não base sem resultar em um texto explicativo não base para hospedar objetos ou para o método [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stidThread`  
 no Identificador do thread a ser interrompido ou um dos seguintes valores de identificador de thread especiais:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Todos os threads. A interrupção é aplicada a todos os métodos de script atualmente em andamento. Observe que, a menos que o chamador solicite que o script seja desconectado, o próximo evento com script faz com que o código do script seja executado novamente chamando o método [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) com o sinalizador SCRIPTSTATE_DISCONNECTED ou SCRIPTSTATE_INITIALIZED Definição.|  
|SCRIPTTHREADID_BASE|O thread base; ou seja, o thread no qual o mecanismo de script foi instanciado.|  
|SCRIPTTHREADID_CURRENT|O thread atualmente em execução.|  
  
 `pexcepinfo`  
 no Endereço de uma estrutura de `EXCEPINFO` que contém as informações de erro que devem ser relatadas ao script anulado.  
  
 `dwFlags`  
 no Sinalizadores de opção associados à interrupção. Pode ser um destes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Se houver suporte, insira o depurador do mecanismo de script no ponto de execução do script atual.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Se houver suporte para o idioma do mecanismo de script, deixe que o script manipule a exceção. Caso contrário, o método de script será anulado e o código de erro será retornado para o chamador; ou seja, a origem do evento ou o chamador de macro.|  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)