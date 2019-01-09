---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bac3b5755328e643c26c8f3746af6648d8ac06aa
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094621"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Recupera um identificador de script-mecanismo-definidas para o thread em execução no momento. O identificador pode ser usado em chamadas subsequentes para métodos de controle de execução do thread de script, como o [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstidThread`  
 [out] Endereço de uma variável que recebe o identificador de thread de script associado ao thread atual. A interpretação desse identificador é deixada para o mecanismo de script, mas ele pode ser apenas uma cópia do identificador de thread do Windows. Se o thread do Win32 for encerrado, esse identificador se torna não atribuído e, posteriormente, pode ser atribuído a outro thread.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se for bem-sucedido, ou `E_POINTER` se um ponteiro inválido foi especificado.  
  
## <a name="remarks"></a>Comentários  
 Esse método pode ser chamado de threads não base sem resultando em um balão não base para objetos de host ou o [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)