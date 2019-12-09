---
title: 'Método IJsDebugDataTarget:: ReadNullTerminatedString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572409"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>Método IJsDebugDataTarget::ReadNullTerminatedString
Lê o número especificado de caracteres do destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 no O endereço do qual ler.  
  
 `characterSize`  
 [no] tamanho de cada caractere na cadeia de caracteres  
  
 `maxCharacters`  
 no O número máximo de caracteres a serem lidos. maxCharacters deve ser razoável. Qualquer solicitação para mais de 128 MB de memória falhará.  Se a cadeia de caracteres for maior que maxCharacters, a cadeia de caracteres de resultado será truncada após maxCharacters.  
  
 `pString`  
 fora O BSTR lido do destino.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Retorna S_FALSE se truncado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)