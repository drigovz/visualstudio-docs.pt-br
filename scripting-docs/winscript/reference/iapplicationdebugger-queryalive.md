---
title: IApplicationDebugger::QueryAlive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b4c455305116863a4a8ad16ff21cd7554a36239
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991187"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Indica se o depurador está respondendo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método indica se o depurador está respondendo. As implementações desse método devem retornar sempre `S_OK`.  
  
 Se o processo do depurador termina inesperadamente, COM retornará um erro do proxy marshaling de chamadas para esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IApplicationDebugger Interface](../../winscript/reference/iapplicationdebugger-interface.md)