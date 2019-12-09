---
title: IDebugAsyncOperation::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573249"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Faz com que a operação assíncrona seja iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `padocb`  
 A interface de retorno de chamada que recebe eventos de status desta operação.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_UNEXPECTED`|Uma operação já está pendente.|  
  
## <a name="remarks"></a>Comentários  
 Esse método faz com que `IDebugSyncOperation::Execute` seja chamado de forma assíncrona no thread obtido do `IDebugSyncOperation::GetTargetThread`. Esse método deve ser chamado somente de dentro do thread do depurador; caso contrário, não retornará até que a operação seja concluída.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
   de [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)