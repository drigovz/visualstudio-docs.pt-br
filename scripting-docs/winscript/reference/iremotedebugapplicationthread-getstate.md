---
title: 'IRemoteDebugApplicationThread:: GetState | Microsoft Docs'
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
ms.openlocfilehash: 42f7f2a292c908b5fe49f1097b0fe56b8b0b11e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575247"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Obtém o estado deste thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pState`  
 fora Combinação dos seguintes sinalizadores de estado de thread:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|O thread está em execução.|  
|THREAD_STATE_SUSPENDED|0x00000002|O thread está suspenso.|  
|THREAD_BLOCKED|0x00000004|O thread está bloqueado.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|O thread está sem conteúdo.|  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método obtém o estado desse thread.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)