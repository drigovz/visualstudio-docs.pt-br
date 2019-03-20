---
title: IDebugFormatter::GetVariantForString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea6cd1f77481282700de492e2857046044a04e2a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155371"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Retorna um tipo VARIANT que contém a cadeia de caracteres fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwstrValue`  
 [in] Cadeia de caracteres para armazenar em uma VARIANTE.  
  
 `pvar`  
 [out] VARIANT contendo `pwstrValue`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna um tipo VARIANT que contém a cadeia de caracteres fornecida.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)