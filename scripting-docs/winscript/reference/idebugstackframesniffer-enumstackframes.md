---
title: IDebugStackFrameSniffer::EnumStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSniffer.EnumStackFrames
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSniffer::EnumStackFrames
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0d6d46a3bbc508308c689b4e10bea15501fad3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005726"
---
# <a name="idebugstackframesnifferenumstackframes"></a>IDebugStackFrameSniffer::EnumStackFrames
Retorna um enumerador dos quadros de pilha do thread atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppedsf`  
 [out] Enumerador de quadros de pilha do thread atual.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O enumerador de quadro de pilha retorna os quadros começando do topo da pilha, começando com o quadro mais recentemente enviados por push.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)