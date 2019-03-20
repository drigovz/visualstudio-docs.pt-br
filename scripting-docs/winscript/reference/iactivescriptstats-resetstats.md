---
title: IActiveScriptStats::ResetStats | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.ResetStats
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::ResetStats
ms.assetid: d98276fc-ad47-4e7b-aae4-254d63aece77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbd18719cde85b12e9ec5de3b19dbf8e81bd8575
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150966"
---
# <a name="iactivescriptstatsresetstats"></a>IActiveScriptStats::ResetStats
Redefine as estatísticas para esse script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ResetStats();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método redefine as estatísticas para esse script.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptStats Interface](../../winscript/reference/iactivescriptstats-interface.md)