---
title: 'IDebugStackFrame:: GetCodeContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetCodeContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetCodeContext
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b640238b9c1212f477c6a26a9cc251678758f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574282"
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
Retorna o contexto do código atual associado ao quadro da pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppcc`  
 fora O contexto de código associado ao registro de ativação.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o contexto de código atual associado ao registro de ativação.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)