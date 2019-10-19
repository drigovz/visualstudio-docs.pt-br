---
title: Interface IMachineDebugManagerCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573881"
---
# <a name="imachinedebugmanagercookie-interface"></a>Interface IMachineDebugManagerCookie
Semelhante à interface `IMachineDebugManager`, a interface `IMachineDebugManagerCookie` dá suporte a cookies de depuração.  
  
 Essa interface (juntamente com a interface `IDebugCookie`) permite que os scripts sejam executados em um processo do depurador de script sem exigir que o depurador acompanhe esses scripts.  
  
 Um depurador de script chama o método `IDebugCookie::SetDebugCookie` no Gerenciador de depuração de processo (PDM). Em seguida, o PDM envia esse cookie junto com qualquer solicitação para adicionar ou remover um aplicativo de script de ou para o MDM (Gerenciador de depuração de máquina), usando os métodos da interface `IMachineDebugManagerCookie`. Em seguida, o MDM notifica todos os depuradores da alteração, exceto para aquele que tem esse cookie.  
  
 Além dos métodos herdados de `IUnknown`, a interface `IMachineDebugManagerCookie` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Adiciona um aplicativo à lista de aplicativos em execução.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Retorna um enumerador da lista atual de aplicativos em execução.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Remove um aplicativo da lista de aplicativos em execução.|  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
 [Interface IDebugCookie](../../winscript/reference/idebugcookie-interface.md)