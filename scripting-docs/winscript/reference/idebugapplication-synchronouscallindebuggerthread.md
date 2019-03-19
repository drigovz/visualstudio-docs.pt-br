---
title: IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5460efaa3448c7812707e0baa7b2f5afe1d27a0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154018"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fornece um mecanismo para que o chamador executar o código no thread do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pptc`  
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
 Hosts e mecanismos de linguagem normalmente usam esse método para implementar os objetos de thread livre sobre suas implementações de threads únicos.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)