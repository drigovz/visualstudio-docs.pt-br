---
title: Enumeração SCRIPTTHREADSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b4cebacf553b38e1edcbff66b6d17bc14156b10f
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238771"
---
# <a name="scriptthreadstate-enumeration"></a>Enumeração SCRIPTTHREADSTATE
Especifica o estado de um thread em um mecanismo de script. Essa enumeração é usada pelo método [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|Valor|Estado do thread de script|  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|O thread especificado não está atendendo atualmente a um evento com script, processando imediatamente o texto do script ou executando uma macro de script.|  
|SCRIPTTHREADSTATE_RUNNING|O thread especificado está atendendo ativamente a um evento com script, processando imediatamente o texto do script ou executando uma macro de script.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)