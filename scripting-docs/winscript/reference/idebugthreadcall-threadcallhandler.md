---
title: 'IDebugThreadCall:: ThreadCallHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugThreadCall.ThreadCallHandler
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugThreadCall::ThreadCallHandler
ms.assetid: c6d5d9db-bfed-44ec-90bc-46637f7de0ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 58e7d3facbd5a59bf7b81e3257c6daea7874141a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576650"
---
# <a name="idebugthreadcallthreadcallhandler"></a>IDebugThreadCall::ThreadCallHandler
Manipula chamadas para executar código em outro thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ThreadCallHandler(  
   DWORD_PTR  dwParam1,  
   DWORD_PTR  dwParam2,  
   DWORD_PTR  dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwParam1`  
 no O primeiro parâmetro.  
  
 `dwParam2`  
 no O segundo parâmetro.  
  
 `dwParam3`  
 no O terceiro parâmetro.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método manipula chamadas para executar o código no thread do depurador.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)  
 [IDebugApplication:: SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)    
 [IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)