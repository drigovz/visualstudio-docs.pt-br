---
title: IDebugAsyncOperation::GetResult | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d86e9eb2b934bc6bd4027405d06960cd107f81c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087471"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Fornece o valor de retorno e parâmetro de objeto de retorno da operação de depuração síncrona.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phrResult`  
 [out] Se a operação for concluída, `phrResult` é o valor de retorno `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Se a operação for concluída, `ppunkResult` é o parâmetro de objeto retornado pela operação.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_PENDING`|A operação não foi concluída.|  
  
## <a name="remarks"></a>Comentários  
 Se a operação for concluída, esse método retorna o `HRESULT` e o parâmetro a partir do objeto `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)