---
title: 'IEnumDebugStackFrames:: clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Clone
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f812176406b234160883956c3311d8c05a75b743
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570886"
---
# <a name="ienumdebugstackframesclone"></a>IEnumDebugStackFrames::Clone
Cria um enumerador que contém o mesmo estado que o enumerador atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppedsf`  
 fora Retorna a interface `IEnumDebugStackFrames` do clone do enumerador.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um enumerador que contém o mesmo estado que o enumerador atual.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)