---
title: 'IDebugExpression:: iniciar | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576436"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Inicia a avaliação da expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdecb`  
 no Retorno de chamada para indicar quando a avaliação da expressão foi concluída. Se esse parâmetro for `NULL`, nenhum evento será acionado e o cliente deverá sondar o estado da expressão usando `QueryIsComplete`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método inicia a avaliação da expressão.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpression:: Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)