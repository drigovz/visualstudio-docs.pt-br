---
title: Enumeração BREAKPOINT_STATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: faca5ef7bc89bc16d646f66fb897f1dc44eb831a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955354"
---
# <a name="breakpointstate-enumeration"></a>Enumeração BREAKPOINT_STATE
Indica o estado de um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|BREAKPOINT_DELETED|O ponto de interrupção não existe mais, mas ainda há referências a ele.|  
|BREAKPOINT_DISABLED|O ponto de interrupção existe, mas está desabilitado.|  
|BREAKPOINT_ENABLED|O ponto de interrupção existe e está habilitado.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)