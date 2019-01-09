---
title: Constantes SCRIPTTHREADID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27852f97cf0a78919b10043c64b1c5a7cc7d3ec5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097806"
---
# <a name="scriptthreadid-constants"></a>Constantes SCRIPTTHREADID
Usado para especificar o tipo de thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|O thread em execução no momento.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|O thread base. ou seja, o thread no qual o script do mecanismo foi instanciado.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Todos os threads.|  
  
## <a name="remarks"></a>Comentários  
 O `SCRIPTTHREADID` tipo é usado pelo `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, e `IActiveScript::InterruptScriptThread`, mas as constantes podem ser usadas somente por `IActiveScript::GetScriptThreadState` e `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)