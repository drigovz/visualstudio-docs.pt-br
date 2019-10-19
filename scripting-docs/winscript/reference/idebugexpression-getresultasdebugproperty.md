---
title: 'IDebugExpression:: GetResultAsDebugProperty | Microsoft Docs'
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
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575921"
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
 fora O valor de retorno da operação.  
  
 `ppdp`  
 fora A propriedade de depuração para a expressão.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_PENDING`|A operação ainda está pendente.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o resultado da avaliação da expressão como uma `IDebugProperty` e a `HRESULT` da operação.  
  
 Esse método retornará `S_OK` e `phrResult` retornará `E_ABORT` se `Abort` abortar a operação.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)