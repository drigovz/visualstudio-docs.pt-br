---
title: 'Método ijsenumdebugproperty:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9e6b0e3499f9420d42660880f616d2d0873d7a0f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086769"
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