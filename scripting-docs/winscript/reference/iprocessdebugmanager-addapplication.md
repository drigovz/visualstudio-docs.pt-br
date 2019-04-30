---
title: IProcessDebugManager::AddApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.AddApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 206baa92ae8d2803b2b07f4966565755a1785d61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944969"
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Adiciona um aplicativo à lista do Gerenciador de depuração de máquina dos aplicativos em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pda`  
 [in] O aplicativo de depuração para adicionar à lista de aplicativos em execução.  
  
 `pdwAppCookie`  
 [out] Um cookie que é usado para remover o aplicativo do Gerenciador de depuração de máquina.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método adiciona um aplicativo para a execução a lista de aplicativos no Gerenciador de depuração do computador.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)