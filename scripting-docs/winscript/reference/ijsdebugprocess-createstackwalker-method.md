---
title: 'Método ijsdebugprocess:: Createstackwalker | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb084b665467ae023bb885ee0de221f0409a0160
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557727"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>Método IJsDebugProcess::CreateStackWalker
Método de fábrica para movimentador de pilhas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadId`  
 [in] A ID do thread.  
  
 `ppStackWalker`  
 [out] O novo objeto de movimentador de pilha.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retornará E_JsDEBUG_UNKNOWN_THREAD se o thread não tiver JavaScript nele. Esse método só pode ser chamado enquanto o processo de destino é interrompido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)