---
title: IEnumDebugApplicationNodes::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Reset
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Reset
ms.assetid: 56ecdafe-ff11-461a-92e1-93254a49f1a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 960f980bda330eaf14cc498e8bf804649023ba39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951717"
---
# <a name="ienumdebugapplicationnodesreset"></a>IEnumDebugApplicationNodes::Reset
Redefine uma sequência de enumeração para o início.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método redefine uma sequência de enumeração para o início.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)