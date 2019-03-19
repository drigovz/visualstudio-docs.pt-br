---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
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
ms.openlocfilehash: d329e08e6a17d9edcdf26e14b468c3c56f036c00
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154394"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Recupera um identificador de script-mecanismo-definidas para o thread associado o determinado thread Win32.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwWin32ThreadID` ,  
 [in] Identificador de thread de um thread do Win32 em execução no processo atual. Use o [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) função para recuperar o identificador de thread do thread em execução no momento.  
  
 `pstidThread` ,  
 [out] Endereço de uma variável que recebe o identificador de thread de script associado o determinado thread do Win32. A interpretação desse identificador é deixada para o mecanismo de script, mas ele pode ser apenas uma cópia do identificador de thread do Windows. Observe que, se o thread do Win32 for encerrado, este identificador se torna não atribuído e, posteriormente, pode ser atribuído a outro thread.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado) e, portanto, com falha.|  
  
## <a name="remarks"></a>Comentários  
 O identificador recuperado pode ser usado em chamadas subsequentes para métodos de controle de execução de thread de script, como o [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) método.  
  
 Esse método pode ser chamado de threads não base sem resultando em um balão não base para objetos de host ou o [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)