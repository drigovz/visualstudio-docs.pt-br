---
title: IDebugExpression::GetResultAsDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06d9b513d40450e20bb87f07c460bef7ce2678c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978484"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Retorna o resultado da avaliação da expressão como uma propriedade de depuração e o valor de retorno da operação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phrResult`  
 [out] Valor de retorno da operação.  
  
 `ppdp`  
 [out] A propriedade de depuração para a expressão.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_PENDING`|A operação ainda está pendente.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o resultado da avaliação da expressão como uma `IDebugProperty` e a operação `HRESULT`.  
  
 Esse método retornará `S_OK` e `phrResult` retorna `E_ABORT` se `Abort` anula a operação.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)