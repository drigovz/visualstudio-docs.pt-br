---
title: IDebugApplication::GetCurrentThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetCurrentThread
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0712994881aaa58e41246bc054ba6cee895ae0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092151"
---
# <a name="idebugapplicationgetcurrentthread"></a>IDebugApplication::GetCurrentThread
Retorna o thread associado ao thread em execução no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pat`  
 [out] O thread associado ao thread em execução no momento.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o thread associado ao thread em execução no momento.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md)