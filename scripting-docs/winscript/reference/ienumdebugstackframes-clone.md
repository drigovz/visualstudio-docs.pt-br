---
title: IEnumDebugStackFrames::Clone | Microsoft Docs
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
ms.openlocfilehash: 117ed9923936a7211c1cc871fa084c269bd2a270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963371"
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
 [out] Retorna o `IEnumDebugStackFrames` interface do clone do enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um enumerador que contém o mesmo estado que o enumerador atual.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)