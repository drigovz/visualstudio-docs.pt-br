---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
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
ms.openlocfilehash: aa46bc95087b3defaf739cc3473c58e29a93071c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155924"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrompe a execução de um thread em execução do script (um coletor de eventos, uma execução imediata ou uma invocação de macro). Esse método pode ser usado para encerrar um script que está preso (por exemplo, em um loop infinito). Ele pode ser chamado de threads não base sem resultando em um balão não base para objetos de host ou o [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) método.  
  
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
 [in] Identificador do thread para interrupção ou um dos seguintes valores de identificador de thread especial:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Todos os threads. A interrupção é aplicada a todos os métodos de script está em andamento. Observe que, a menos que o chamador solicitou que o script a ser desconectada, o próximo evento com script faz com que o código de script executar novamente com a chamada a [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) método com o SCRIPTSTATE_DISCONNECTED ou O sinalizador SCRIPTSTATE_INITIALIZED definido.|  
|SCRIPTTHREADID_BASE|O thread base. ou seja, o thread no qual o script do mecanismo foi instanciado.|  
|SCRIPTTHREADID_CURRENT|O thread em execução no momento.|  
  
 `pexcepinfo`  
 [in] Endereço de um `EXCEPINFO` estrutura que contém as informações de erro devem ser relatadas para o script anulado.  
  
 `dwFlags`  
 [in] Sinalizadores de opção associados com a interrupção. Pode ser um destes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Se houver suporte, insira o depurador do mecanismo de script no ponto de execução de script atual.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Se o suporte para a linguagem do mecanismo de script, permitem que o script de tratar a exceção. Caso contrário, o método de script será anulado e o código de erro é retornado ao chamador; ou seja, o evento fonte ou macro chamador.|  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)