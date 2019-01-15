---
title: 'Idiaframedata:: Get_allocatesbasepointer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3ce39d0fb64cdd89139bb4506c9b95719a3f172
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951309"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Recupera um sinalizador que indica se o ponteiro de base está alocado para o código nesse intervalo de endereço. Este método foi preterido.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se um ponteiro de base é alocado; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Essa propriedade deve ser usada somente pelo código que anteriormente acessados FPO_DATA ou quando a cadeia de caracteres do programa é retornada pelo [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) método é `NULL`. Caso contrário, a cadeia de caracteres do programa contém todas as informações necessárias para computar os valores de registro anterior.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)