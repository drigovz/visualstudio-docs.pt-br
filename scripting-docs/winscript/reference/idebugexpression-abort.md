---
title: 'IDebugExpression:: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Abort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Abort
ms.assetid: dbdb63c1-6c4a-4cef-bb40-1843495ae167
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 508939b23be53acbff269744ae4035853f977ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575942"
---
# <a name="idebugexpressionabort"></a>IDebugExpression::Abort
Interrompe a expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método interrompe uma avaliação de expressão na primeira oportunidade.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)