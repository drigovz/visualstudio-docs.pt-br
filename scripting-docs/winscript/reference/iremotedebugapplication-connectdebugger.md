---
title: 'IRemoteDebugApplication:: ConnectDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed0ddeffd55475e1be4c9fab1e567d61a4b6654
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572324"
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Conecta um depurador a este aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pad`  
 no O depurador a ser anexado a este aplicativo.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|Um depurador já está conectado a este aplicativo.|  
  
## <a name="remarks"></a>Comentários  
 Um aplicativo pode ter apenas um depurador conectado por vez. Esse método falhará se um depurador já estiver conectado.  
  
## <a name="see-also"></a>Consulte também  
 [IRemoteDebugApplication:: getdebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)    
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)