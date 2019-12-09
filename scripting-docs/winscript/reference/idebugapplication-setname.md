---
title: 'IDebugApplication:: SetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SetName
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a3e5115d4adc3fc3dfa93f10c90cb0d2b36f0e4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571107"
---
# <a name="idebugapplicationsetname"></a>IDebugApplication::SetName
Define o nome do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrName`  
 no O nome do aplicativo.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O nome fornecido para esse método é retornado em chamadas subsequentes para o método `IRemoteDebugApplication::GetName`.  
  
 Esse método deve ser chamado antes de chamar o método `IProcessDebugManager::AddApplication`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)