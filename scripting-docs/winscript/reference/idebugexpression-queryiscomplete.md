---
title: IDebugExpression::QueryIsComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b4fa4b027f0ee8d848f52c063cbfd1f7679d4a6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087146"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Determina se a operação for concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido e a operação for concluída.|  
|`S_FALSE`|A operação ainda está pendente.|  
  
## <a name="remarks"></a>Comentários  
 Este método determina se a operação for concluída.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugExpression](../../winscript/reference/idebugexpression-interface.md)