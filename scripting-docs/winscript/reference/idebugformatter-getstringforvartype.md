---
title: IDebugFormatter::GetStringForVarType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 06c4833e2d9a88b63a80b2ee9437dc5547579380
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087536"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
Retorna uma cadeia de caracteres que representa o valor VARTYPE especificado.  
  
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
 [in] VARTYPE para ser representado como uma cadeia de caracteres.  
  
 `ptdescArrayType`  
 [in] Matriz de estruturas que descreve os tipos.  
  
 `pbstr`  
 [out] Cadeia de caracteres que representa `vt`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O método retorna uma cadeia de caracteres que representa o valor VARTYPE especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)