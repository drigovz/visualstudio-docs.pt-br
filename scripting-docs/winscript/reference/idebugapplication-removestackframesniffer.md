---
title: 'IDebugApplication:: RemoveStackFrameSniffer | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605daf51214ba5af9d6010b28be9569453ca7962
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571117"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Remove um provedor de enumerador de quadros de pilha deste aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCookie`  
 no O cookie retornado pelo método `AddStackFrameSniffer` quando o provedor de enumerador de quadros de pilha foi adicionado.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O método `RemoveStackFrameSniffer` remove um provedor de enumerador de quadros de pilha deste aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication:: AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)    
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)