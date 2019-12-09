---
title: 'IDebugApplication:: SynchronousCallInDebuggerThread | Microsoft Docs'
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
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574582"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fornece um mecanismo para o chamador executar o código no thread do depurador.  
  
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
 no O objeto a ser chamado.  
  
 `dwParam1`  
 no Primeiro parâmetro a ser passado para o método `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 no Segundo parâmetro a ser passado para o método `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 no Terceiro parâmetro a ser passado para o método `IDebugThreadCall::ThreadCallHandler`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Os hosts e os mecanismos de linguagem normalmente usam esse método para implementar objetos de thread livre sobre suas implementações de thread único.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)