---
title: 'IObjectIdentity:: isequalobject | Microsoft Docs'
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
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571467"
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
 no Endereço do objeto a ser comparado com o objeto atual.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|Os objetos são iguais.|  
|`S_FALSE`|Os objetos não são iguais.|  
  
## <a name="remarks"></a>Comentários  
 Uma implementação do método `IsEqualObject` deve retornar `S_OK` somente se os objetos forem idênticos.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)