---
title: IRemoteDebugApplicationThread::GetState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6534f57c92776dcd3cde9083335becbd66002a32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788111"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Obtém o estado desse thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pState`  
 [out] Combinação dos seguintes sinalizadores de estado do thread:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|O thread está em execução.|  
|THREAD_STATE_SUSPENDED|0x00000002|O thread está suspenso.|  
|THREAD_BLOCKED|0x00000004|O thread está bloqueado.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|O thread está fora do conteúdo.|  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método obtém o estado desse thread.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)