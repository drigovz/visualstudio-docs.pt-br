---
title: 'Método ijsenumdebugproperty:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ec6a1dded8c24de06a5746261a19b6609a97ada
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977533"
---
# <a name="ijsenumdebugpropertynext-method"></a>Método IJsEnumDebugProperty::Next
Lê propriedades para este objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `count`  
 [in] O número de propriedades a serem lidas.  
  
 `ppDebugProperty`  
 [out] Objeto que representa o navegador de propriedade.  
  
 `pActualCount`  
 [out] O número real de propriedades do objeto.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)