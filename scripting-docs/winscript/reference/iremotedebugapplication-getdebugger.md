---
title: IRemoteDebugApplication::GetDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ddb6ac5ab9f8597b1f8d22924bdd57204f66c359
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095440"
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
 [out] O depurador atual conectado ao aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o depurador atual conectado ao aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)   
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)