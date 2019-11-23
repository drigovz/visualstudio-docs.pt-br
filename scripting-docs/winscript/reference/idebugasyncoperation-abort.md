---
title: 'IDebugAsyncOperation:: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573305"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Cancela uma operação.  
  
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
|S_OK|O método foi bem-sucedido.|  
|E_NOTIMPL|As operações não podem ser canceladas.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é normalmente chamado de dentro do thread do depurador para cancelar uma operação sem resposta. Esse método faz com que o método `InProgressAbort` no objeto `IDebugSyncOperation` seja chamado.  
  
## <a name="see-also"></a>Consulte também  
   de [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)