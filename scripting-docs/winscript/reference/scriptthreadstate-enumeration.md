---
title: Enumeração SCRIPTTHREADSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c66d078effd510b3f64cf1f443926984ff2e282
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094114"
---
# <a name="scriptthreadstate-enumeration"></a>Enumeração SCRIPTTHREADSTATE
Especifica o estado de um thread em um mecanismo de script. Essa enumeração é usada pelo [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Thread especificado atualmente não está atendendo a um evento com script, o texto do script de processamento executado imediatamente, ou executando uma macro de script.|  
|SCRIPTTHREADSTATE_RUNNING|Thread especificado está ativamente atendendo a um evento com script, o texto do script de processamento executado imediatamente, ou executando uma macro de script.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)