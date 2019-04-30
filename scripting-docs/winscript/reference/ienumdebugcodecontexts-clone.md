---
title: IEnumDebugCodeContexts::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Clone
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a08c65a7be5ed0b6394ef5e0aab284a03a52a240
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951448"
---
# <a name="ienumdebugcodecontextsclone"></a>IEnumDebugCodeContexts::Clone
Cria um enumerador que contém o mesmo estado que o enumerador atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppescc`  
 [out] Retorna o `IEnumDebugCodeContexts` interface do clone do enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria um enumerador que contém o mesmo estado que o enumerador atual.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)