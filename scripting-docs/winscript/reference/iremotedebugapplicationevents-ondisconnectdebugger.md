---
title: IRemoteDebugApplicationEvents::OnDisconnectDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnDisconnectDebugger
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnDisconnectDebugger
ms.assetid: ea11cde0-1484-4181-a5dd-a1f6cf788892
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d99ef6b4bcbafc78fd3e6ebcdc2c4129c3653a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934573"
---
# <a name="iremotedebugapplicationeventsondisconnectdebugger"></a>IRemoteDebugApplicationEvents::OnDisconnectDebugger
Evento de desconexão de identificadores de um depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnDisconnectDebugger();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método trata o depurador do evento de desconexão.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)