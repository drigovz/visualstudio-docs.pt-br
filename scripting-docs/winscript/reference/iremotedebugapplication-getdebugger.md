---
title: 'IRemoteDebugApplication:: getdebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetDebugger
ms.assetid: 3d173b86-9281-4a3c-9550-d79408fd50ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 031e4390941d9b8b025c704ebfcec20224aa1c79
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573826"
---
# <a name="iremotedebugapplicationgetdebugger"></a>IRemoteDebugApplication::GetDebugger
Retorna o depurador atual conectado ao aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDebugger(  
   IApplicationDebugger**  pad  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pad`  
 fora O depurador atual conectado ao aplicativo.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o depurador atual conectado ao aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [IRemoteDebugApplication:: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)    
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)