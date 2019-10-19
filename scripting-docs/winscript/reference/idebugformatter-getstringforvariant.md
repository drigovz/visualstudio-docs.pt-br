---
title: 'IDebugFormatter:: GetStringForVariant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f703396190f1fb7791306ee9e389b676e749f8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576362"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Retorna uma cadeia de caracteres que representa o valor da variante fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvar`  
 no VARIANT para representar como uma cadeia de caracteres.  
  
 `nRadix`  
 no Radix a ser usado para valores numéricos.  
  
 `pbstrValue`  
 fora Cadeia de caracteres que representa `pvar`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna uma cadeia de caracteres que representa o valor da variante fornecido.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)