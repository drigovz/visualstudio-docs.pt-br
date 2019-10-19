---
title: 'IEnumDebugExtendedPropertyInfo:: clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Clone
ms.assetid: dd645cf6-bfb3-486c-829e-bb91a6639665
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d11aa307342fbb6029f3bc2aed6b652417f4f52d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568910"
---
# <a name="ienumdebugextendedpropertyinfoclone"></a>IEnumDebugExtendedPropertyInfo::Clone
Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Clone (  
   IEnumDebugExtendedPropertyInfo** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 fora Retorna a interface de `IEnumDebugExtendedPropertyInfo` clonada.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)