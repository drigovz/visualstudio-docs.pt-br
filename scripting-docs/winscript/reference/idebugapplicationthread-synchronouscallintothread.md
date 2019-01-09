---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5e25f42b2bce66cf3bb7ab3e69d3711e2526ae1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097052"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Fornece um mecanismo para que o chamador executar o código no thread do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstcb`  
 [in] Objeto a ser chamado.  
  
 `dwParam1`  
 [in] O primeiro parâmetro para passar para o `IDebugThreadCall::ThreadCallHandler` método.  
  
 `dwParam2`  
 [in] Segundo parâmetro para passar para o `IDebugThreadCall::ThreadCallHandler` método.  
  
 `dwParam3`  
 [in] Terceiro parâmetro para passar para o `IDebugThreadCall::ThreadCallHandler` método.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método fornece um mecanismo para que o chamador executar o código no thread do depurador. Hosts e mecanismos de linguagem normalmente usam esse método para implementar os objetos de thread livre sobre suas implementações de threads únicos.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)