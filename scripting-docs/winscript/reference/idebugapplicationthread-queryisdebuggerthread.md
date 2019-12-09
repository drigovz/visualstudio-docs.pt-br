---
title: 'IDebugApplicationThread:: QueryIsDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsDebuggerThread
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: febce73e2c40d0df02acc42f6219eca30afb3f29
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574541"
---
# <a name="idebugapplicationthreadqueryisdebuggerthread"></a>IDebugApplicationThread::QueryIsDebuggerThread
Determina se este thread é o thread do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT QueryIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido e este é o thread do depurador.|  
|`S_FALSE`|Este não é o thread do depurador.|  
  
## <a name="remarks"></a>Comentários  
 Esse método determina se esse thread é o thread do depurador.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)