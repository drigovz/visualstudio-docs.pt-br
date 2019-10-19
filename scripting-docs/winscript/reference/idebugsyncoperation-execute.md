---
title: 'IDebugSyncOperation:: execute | Microsoft Docs'
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
ms.openlocfilehash: 25da02e6736cc2f8ac27c82f922bd515e791bef1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576691"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Executa de forma síncrona a operação e retorna.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppunkResult`  
 fora O parâmetro de objeto retornado pela operação.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_ABORT`|A operação foi anulada chamando o método `IDebugSyncOperation::InProgressAbort`.|  
  
## <a name="remarks"></a>Comentários  
 O Gerenciador de depuração de processos no thread de destino chama o método `Execute` de forma síncrona.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)