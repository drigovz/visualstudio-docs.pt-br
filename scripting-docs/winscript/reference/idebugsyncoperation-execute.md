---
title: IDebugSyncOperation::Execute | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2bc204169ff94a240e363eb8caa35ec8c7de9be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004869"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Forma síncrona executa a operação e retorna.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppunkResult`  
 [out] O parâmetro de objeto retornado pela operação.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_ABORT`|A operação foi anulada, chamando o `IDebugSyncOperation::InProgressAbort` método.|  
  
## <a name="remarks"></a>Comentários  
 O Gerenciador de depuração do processo nas chamadas do thread de destino a `Execute` método forma síncrona.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)