---
title: 'Método ijsdebugdatatarget:: Readnullterminatedstring | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a681dcedf873f0cb96f47b14278f47271cd43ec8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093321"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>Método IJsDebugDataTarget::ReadNullTerminatedString
Lê o número especificado de caracteres de destino.  
  
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
 [in] O endereço de onde ler.  
  
 `characterSize`  
 [in] tamanho de cada caractere na cadeia de caracteres  
  
 `maxCharacters`  
 [in] O número máximo de caracteres a serem lidos. maxCharacters deve ser razoável. Qualquer solicitação para mais de 128MB de memória falhará.  Se a cadeia de caracteres for maior do que maxCharacters, a cadeia de caracteres de resultado será truncada após maxCharacters.  
  
 `pString`  
 [out] Leia o BSTR do destino.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retornará S_FALSE se truncado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)