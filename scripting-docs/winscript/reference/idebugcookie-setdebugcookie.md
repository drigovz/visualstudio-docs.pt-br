---
title: IDebugCookie::SetDebugCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c83c1331a95e48afa02b0b37557ca5bd042261d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974469"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
Define o cookie de depuração do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwDebugAppCookie`  
 [in] Um cookie que identifica o aplicativo de depuração.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método define o cookie de depuração do aplicativo, o que permite que mais de um depurador para anexar a um processo.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugCookie](../../winscript/reference/idebugcookie-interface.md)