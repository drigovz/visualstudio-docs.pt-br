---
title: 'Método IJsDebugProcess:: CreateStackWalker | Microsoft Docs'
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
ms.openlocfilehash: 70f5d4885abba3d891526723d3ca1f174549c348
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573835"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>Método IJsDebugProcess::CreateStackWalker
Método de fábrica para o Stack Walker.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadId`  
 no A ID do thread.  
  
 `ppStackWalker`  
 fora O novo objeto Stack Walker.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Retorna E_JsDEBUG_UNKNOWN_THREAD se o thread não tiver um JavaScript nele. Esse método só pode ser chamado enquanto o processo de destino é interrompido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)