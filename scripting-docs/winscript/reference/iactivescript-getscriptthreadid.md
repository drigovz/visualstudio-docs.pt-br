---
title: 'IActiveScript:: GetScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575701"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Recupera um identificador definido por mecanismo de script para o thread associado ao thread Win32 fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwWin32ThreadID`,  
 no Identificador de thread de um Thread Win32 em execução no processo atual. Use a função [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) para recuperar o identificador de thread do thread em execução no momento.  
  
 `pstidThread`,  
 fora Endereço de uma variável que recebe o identificador de thread de script associado ao thread Win32 fornecido. A interpretação desse identificador é deixada para o mecanismo de script, mas pode ser apenas uma cópia do identificador de thread do Windows. Observe que, se o Thread Win32 for encerrado, esse identificador se tornará não atribuído e poderá ser atribuído posteriormente a outro thread.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado) e, portanto, falhou.|  
  
## <a name="remarks"></a>Comentários  
 O identificador recuperado pode ser usado em chamadas subsequentes para métodos de controle de execução de thread de script, como o método [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Esse método pode ser chamado de threads não base sem resultar em um texto explicativo não base para hospedar objetos ou para a interface [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)