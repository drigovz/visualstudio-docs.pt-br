---
title: 'Método ijsdebugstackwalker:: GetNext | Microsoft Docs'
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
ms.openlocfilehash: ba8931a01f3afe05f791f4d89da60a9354868215
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148445"
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
 [out] Objeto que representa o quadro de pilhas.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retornará E_JsDEBUG_OUTSIDE_OF_VM quando não há nenhum quadro de pilha mais a serem enumerados  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)