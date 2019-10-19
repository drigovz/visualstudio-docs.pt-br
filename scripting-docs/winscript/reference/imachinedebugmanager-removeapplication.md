---
title: 'IMachineDebugManager:: RemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::RemoveApplication
ms.assetid: 873509ce-e638-484a-b2a2-489a8ce7dbfe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87951e55a7cfcfef1a366f79c380948c7651ed12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573931"
---
# <a name="imachinedebugmanagerremoveapplication"></a>IMachineDebugManager::RemoveApplication
Remove um aplicativo da lista de aplicativos em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwAppCookie`  
 no O cookie fornecido quando o aplicativo foi adicionado à lista de aplicativos.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado pelo Gerenciador de depuração de processo sempre que `IProcessDebugManager::RemoveApplication` é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IMachineDebugManager:: AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)    
 @No__t_1 de [interface IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)