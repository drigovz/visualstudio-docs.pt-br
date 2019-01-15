---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e139bceb9456e792ddf10d00d8b519a7677cc22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834055"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Designa os tipos de conversão.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elementos  
 THUNK_ORDINAL_NOTYPE  
 Conversão padrão.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Um `this` thunk adjustor.  
  
 THUNK_ORDINAL_VCALL  
 Conversão de chamada virtual.  
  
 THUNK_ORDINAL_PCODE  
 Conversão de código de P.  
  
 THUNK_ORDINAL_LOAD  
 Conversão de carregamento de atraso.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Conversão de trampoline incremental (uma conversão trampoline é usada para chamadas de rejeição do espaço de memória para outro).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Conversão de trampoline do ponto de ramificação.  
  
## <a name="remarks"></a>Comentários  
 Os valores nesta enumeração são retornados de uma chamada para o [idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)