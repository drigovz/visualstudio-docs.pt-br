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
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977676"
---
# <a name="imachinedebugmanagercookie-interface"></a>Interface IMachineDebugManagerCookie
Semelhante do `IMachineDebugManager` interface, o `IMachineDebugManagerCookie` interface dá suporte a cookies de depuração.  
  
 Essa interface (juntamente com o `IDebugCookie` interface) que scripts sejam executados em um processo do depurador de script sem a necessidade de que o depurador manter o controle desses scripts.  
  
 Um depurador de script chama o `IDebugCookie::SetDebugCookie` método sobre o processo de depuração PDM (Gerenciador de). Em seguida, o PDM envia esse cookie junto com qualquer solicitação para adicionar ou remover um aplicativo de script para ou da máquina depurar Manager (MDM), usando os métodos do `IMachineDebugManagerCookie` interface. O MDM notifica cada depurador da alteração, exceto aquele que tem esse cookie.  
  
 Além dos métodos herdados de `IUnknown`, o `IMachineDebugManagerCookie` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Adiciona um aplicativo para a execução lista de aplicativos.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Retorna um enumerador da lista atual de aplicativos em execução.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Remove um aplicativo de execução de lista de aplicativos.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Interface IDebugCookie](../../winscript/reference/idebugcookie-interface.md)