---
title: 'IDebugAsyncOperation:: GetResult | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573291"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Fornece o valor de retorno e o parâmetro de objeto de retorno da operação de depuração síncrona.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phrResult`  
 fora Se a operação for concluída, `phrResult` será o valor de retorno de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 fora Se a operação for concluída, `ppunkResult` será o parâmetro de objeto retornado pela operação.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_PENDING`|A operação não foi concluída.|  
  
## <a name="remarks"></a>Comentários  
 Se a operação for concluída, esse método retornará o `HRESULT` e o parâmetro de objeto de `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)