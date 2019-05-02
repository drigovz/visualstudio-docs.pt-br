---
title: Enumeração BREAKRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5c79aacc64eb57282bf09f7e4673980396b37ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955283"
---
# <a name="breakresumeaction-enumeration"></a>Enumeração BREAKRESUMEACTION
Descreve maneiras de continuar de um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Interrompe o aplicativo.|  
|BREAKRESUMEACTION_CONTINUE|Continua sendo executado.|  
|BREAKRESUMEACTION_STEP_INTO|Etapas em um procedimento.|  
|BREAKRESUMEACTION_STEP_OVER|Etapas em um procedimento.|  
|BREAKRESUMEACTION_STEP_OUT|Etapas do procedimento atual.|  
|BREAKRESUMEACTION_IGNORE|Continua a ser executado com estado.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Etapas para o próximo documento.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)