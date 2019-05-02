---
title: IObjectIdentity::IsEqualObject | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c215a15a1239f07272079783366a1617c3a626e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944885"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Determina se um objeto é igual ao objeto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `punk`  
 [in] Endereço do objeto a ser comparado com o objeto atual.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|Os objetos são iguais.|  
|`S_FALSE`|Os objetos não forem iguais.|  
  
## <a name="remarks"></a>Comentários  
 Uma implementação de `IsEqualObject` método deverá retornar `S_OK` somente se os objetos são idênticos.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)