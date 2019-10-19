---
title: 'IMachineDebugManager:: AddApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ff617ac96c0eb3498b796d4f7fe49f95e1cc96
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573962"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Adiciona um aplicativo à lista de aplicativos em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pda`  
 no Aplicativo para a lista de aplicativos em execução.  
  
 `pdwAppCookie`  
 fora Um cookie que é usado para remover o aplicativo do Machine Debug Manager.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado pelo Gerenciador de depuração de processo sempre que `IProcessDebugManager::AddApplication` é chamado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IMachineDebugManager:: RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)