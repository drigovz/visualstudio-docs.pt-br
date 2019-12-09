---
title: 'IDebugStackFrame:: GetThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetThread
ms.assetid: ece24728-a6b2-4b01-a6f0-0a82b15be39b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51cb000ef20877f4f3f6536cc9a01ae44c2810c8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576730"
---
# <a name="idebugstackframegetthread"></a>IDebugStackFrame::GetThread
Retorna o thread associado a este quadro de pilhas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetThread(  
   IDebugApplicationThread**  ppat  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppat`  
 fora O thread associado a este quadro de pilhas.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o thread associado a esse quadro de pilhas.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)