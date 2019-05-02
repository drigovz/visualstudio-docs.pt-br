---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84255e364630245564a0cbab5d38c6dff38df0a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978465"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Retorna o resultado da avaliação da expressão como uma cadeia de caracteres e o valor de retorno da operação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phrResult`  
 [out] Valor de retorno da operação.  
  
 `pbstrResult`  
 [out] O resultado da avaliação de expressão.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_PENDING`|A operação ainda está pendente.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o resultado da avaliação da expressão como uma cadeia de caracteres e a operação `HRESULT`.  
  
 Esse método retornará `S_OK` e `phrResult` retorna `E_ABORT` se `Abort` anula a operação.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)