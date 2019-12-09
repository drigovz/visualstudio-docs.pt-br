---
title: 'IDebugAsyncOperationCallBack:: OnComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a15ae57d64d2b1e7be867c20e9683e4aaa415974
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573235"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Sinaliza que um resultado está disponível em uma operação de depuração assíncrona.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método sinaliza que um resultado está disponível em um objeto `IDebugAsyncOperation`. O evento é acionado no thread do depurador.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugAsyncOperationCallBack](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
 [IDebugAsyncOperation Interface](../../winscript/reference/idebugasyncoperation-interface.md)