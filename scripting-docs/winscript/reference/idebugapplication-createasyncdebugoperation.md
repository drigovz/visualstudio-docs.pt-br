---
title: 'IDebugApplication:: CreateAsyncDebugOperation | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575568"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Fornece acesso assíncrono a uma determinada operação de depuração síncrona.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `psdo`  
 no O objeto de operação de depuração síncrona.  
  
 `ppado`  
 fora O objeto de operação de depuração assíncrona.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que os mecanismos de linguagem avaliem expressões de forma assíncrona sem sincronizar explicitamente com o thread do depurador. Para obter mais informações, consulte [interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) e [interface IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 @No__t_1 de [interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)  
 [IDebugAsyncOperation Interface](../../winscript/reference/idebugasyncoperation-interface.md)