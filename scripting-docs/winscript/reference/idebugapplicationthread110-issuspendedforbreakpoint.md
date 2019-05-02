---
title: IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82b8957ae9f2b6674af7addf2239c745115e4e3f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440534"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
Determina se [IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) foi chamado nesse thread e ainda não foi concluída.  
  
> [!IMPORTANT]
> [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) é implementada pelo PDM v11.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfIsSuspended`  
 [out] `true` se o thread está suspenso para um ponto de interrupção, caso contrário, `false`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)