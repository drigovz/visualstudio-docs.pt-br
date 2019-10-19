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
ms.openlocfilehash: 47b48b917ee3376c417beffd9972d76a444513ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573200"
---
# <a name="idebugcookie-interface"></a>Interface IDebugCookie
Permite que o cookie de depuração seja definido para uso com a interface `IMachineDebugManagerCookie`. Para obter mais informações, consulte [interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md). Essa interface é implementada pelo PDM (Gerenciador de depuração de processos) e consumida por depuradores de script.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, a interface `IDebugCookie` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Define o cookie do aplicativo de depuração.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)