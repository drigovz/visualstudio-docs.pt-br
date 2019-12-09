---
title: 'IDebugApplicationThreadEvents110:: OnSuspendForBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d73d7769dd48889a75da63da64be1d2977a088
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573341"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Determina se o thread foi suspenso completamente para um ponto de interrupção e ainda não retomou a execução normal.  
  
> [!IMPORTANT]
> A [interface IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Este método não tem parâmetros.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md)