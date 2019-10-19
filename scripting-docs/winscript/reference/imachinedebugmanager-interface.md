---
title: Interface IMachineDebugManager | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManager interface
ms.assetid: 0b7133bb-5a52-4036-b4db-d69260790db7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d491b03ba04d346e3a14a08d5e2b6b9d34c7d97
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573930"
---
# <a name="imachinedebugmanager-interface"></a>Interface IMachineDebugManager
A interface primária para o Machine Debug Manager. Essa interface é semelhante à interface de `IMachineDebugManagerCookie`.  
  
 Além dos métodos herdados de `IUnknown`, a interface `IMachineDebugManager` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|Adiciona um aplicativo à lista de aplicativos em execução.|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|Remove um aplicativo da lista de aplicativos em execução.|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|Retorna um enumerador da lista atual de aplicativos em execução.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)