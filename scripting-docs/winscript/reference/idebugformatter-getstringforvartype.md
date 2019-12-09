---
title: 'IDebugFormatter:: GetStringForVarType | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVarType
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b498f5b37a9fc34b0926d9c0a5601d89dde7c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576354"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
Retorna uma cadeia de caracteres que representa o valor de VARTYPE fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `vt`  
 no VARTYPE para representar como uma cadeia de caracteres.  
  
 `ptdescArrayType`  
 no Matriz de estruturas que descreve os tipos.  
  
 `pbstr`  
 fora Cadeia de caracteres que representa `vt`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O método retorna uma cadeia de caracteres que representa o valor de VARTYPE fornecido.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)