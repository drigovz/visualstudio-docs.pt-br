---
title: IDebugAsyncOperation::QueryIsComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90d054eb6f7e98a604815c559bee4e326b19692d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092931"
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
Determina se a operação de depuração foi concluída.  
  
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
|`S_OK`|A operação é concluída.|  
|`S_FALSE`|A operação não foi concluída.|  
  
## <a name="remarks"></a>Comentários  
 Este método determina se a operação de depuração foi concluída.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAsyncOperation Interface](../../winscript/reference/idebugasyncoperation-interface.md)