---
title: Interface IDebugCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ee129526113a1c8af8f918de81c1f286d5cb703
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154459"
---
# <a name="idebugcookie-interface"></a>Interface IDebugCookie
Permite que o cookie de depuração a ser definido para uso com o `IMachineDebugManagerCookie` interface. Para obter mais informações, consulte [IMachineDebugManagerCookie Interface](../../winscript/reference/imachinedebugmanagercookie-interface.md). Essa interface é implementada pelo processo de depuração PDM (Gerenciador de) e consumida por depuradores de script.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, o `IDebugCookie` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Define o cookie de depuração do aplicativo.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)