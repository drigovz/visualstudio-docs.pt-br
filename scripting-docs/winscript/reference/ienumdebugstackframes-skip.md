---
title: 'IEnumDebugStackFrames:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29e5864d1304aeb4c916e93da8b151336596d979
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575533"
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
Ignora um número especificado de segmentos em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 no Número de segmentos na sequência de enumeração a serem ignorados.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método ignora um número especificado de segmentos em uma sequência de enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)