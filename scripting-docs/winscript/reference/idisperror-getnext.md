---
title: 'IDispError:: GetNext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81186e6eba7983a1210e5de5bca5d83dd77089da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573110"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Recupera o próximo objeto `IDispError`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppde`  
 fora Especifica o próximo `IDispError` objeto.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera o próximo `IDispError` objeto. Se esse for o último objeto `IDispError`, esse método retornará NULL.  
  
> [!NOTE]
> Este método não está implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)