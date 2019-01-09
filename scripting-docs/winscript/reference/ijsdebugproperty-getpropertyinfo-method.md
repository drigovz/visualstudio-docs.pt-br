---
title: 'Método ijsdebugproperty:: Getpropertyinfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: ab9d6e0b-0448-4f21-b0b0-1738867587d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85dd11fbd5b7f012dc47e170ee785e671d6a7f14
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086704"
---
# <a name="ijsdebugpropertygetpropertyinfo-method"></a>Método IJsDebugProperty::GetPropertyInfo
Obtém informações para este objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetPropertyInfo(  
   UINT nRadix,  
   JsDebugPropertyInfo *pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nRadix`  
 [in] Raiz a ser usada.  
  
 `pPropertyInfo`  
 [out] Informações sobre o objeto.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)