---
title: 'Método IJsDebugStackWalker:: GetNext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugStackWalker.GetNext
apilocation:
- jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa667402b46a3404c31dfe26307a5893c68ffcc0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574026"
---
# <a name="ijsdebugstackwalkergetnext-method"></a>Método IJsDebugStackWalker::GetNext
Obtém o próximo quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppFrame`  
 fora Objeto que representa o quadro de pilha.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Retorna E_JsDEBUG_OUTSIDE_OF_VM quando não há mais quadros de pilha a serem enumerados  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)