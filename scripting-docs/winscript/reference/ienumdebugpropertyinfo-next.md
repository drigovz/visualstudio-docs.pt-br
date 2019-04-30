---
title: IEnumDebugPropertyInfo::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1568d2387422bebc86ce2b035ba997610833e85
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963410"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Recupera um número especificado de `DebugPropertyInfo` estruturas em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de `DebugPropertyInfo`estruturas a serem recuperados.  
  
 `rgelt`  
 [out] Uma matriz de `DebugPropertyInfo` recuperadas de estruturas.  
  
 `pceltFetched`  
 [out] Retorna o número de `DebugPropertyInfo` realmente recuperadas de estruturas.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [Estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)