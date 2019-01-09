---
title: IDebugStackFrame::GetCodeContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 14c7acc9070edb0e63dee8c71cb0b16c5f85e4cd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095609"
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
Retorna o contexto de código atual associado com o quadro de pilhas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppcc`  
 [out] O contexto de código associado ao quadro de pilha.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o contexto de código atual associado com o quadro de pilhas.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)