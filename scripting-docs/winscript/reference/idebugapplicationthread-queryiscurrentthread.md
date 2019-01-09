---
title: IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bbcccc6f3f87ced3b9a5af8fc5febeab020aea0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086457"
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Determina se esse thread é o thread em execução no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido e esse é o thread em execução no momento.|  
|`S_FALSE`|Isso não é o thread em execução no momento.|  
  
## <a name="remarks"></a>Comentários  
 Este método determina se esse thread é o thread em execução no momento.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)