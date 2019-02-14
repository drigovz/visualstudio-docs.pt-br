---
title: IDiaFrameData::get_lengthSavedRegisters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthSavedRegisters method
ms.assetid: dfda4e91-9bfa-4b9d-9133-b73015bfa4d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a4b85c3f98d80039b6d490ccf690b10682f5d04
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950488"
---
# <a name="idiaframedatagetlengthsavedregisters"></a>IDiaFrameData::get_lengthSavedRegisters
Recupera o número de bytes de registros salvos empurrados na pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_lengthSavedRegisters (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o número de bytes de registros salvos.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O valor retornado por esse método normalmente é usado na interpretação de uma cadeia de caracteres do programa (consulte a [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) método para a definição de uma cadeia de caracteres do programa).  
  
## <a name="see-also"></a>Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)