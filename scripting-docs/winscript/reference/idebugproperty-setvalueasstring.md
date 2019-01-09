---
title: IDebugProperty::SetValueAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.SetValueAsString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::SetValueAsString
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b106b1e553d3600d51b8b0fc09a0f8ecd4256abd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097608"
---
# <a name="idebugpropertysetvalueasstring"></a>IDebugProperty::SetValueAsString
Define o valor de uma propriedade de uma determinada cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINTnRadix,  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszValue`  
 [in] O valor a ser definido.  
  
 `nRadix`  
 [in] Base a ser usado na interpretação de todas as informações numéricas.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)