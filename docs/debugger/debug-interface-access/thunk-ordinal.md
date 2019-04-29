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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854443"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Designa os tipos de conversão.

## <a name="syntax"></a>Sintaxe

```C++
typedef enum THUNK_ORDINAL {
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
Conversão THUNK_ORDINAL_NOTYPE padrão.

Um THUNK_ORDINAL_ADJUSTOR `this` thunk adjustor.

Conversão de chamada THUNK_ORDINAL_VCALL Virtual.

Conversão de pseudocódigo THUNK_ORDINAL_PCODE.

Conversão de carregamento de atraso THUNK_ORDINAL_LOAD.

Conversão de trampoline THUNK_ORDINAL_TRAMP_INCREMENTAL Incremental (uma conversão trampoline é usada para chamadas de rejeição do espaço de memória para outro).

Conversão de trampoline ponto THUNK_ORDINAL_TRAMP_BRANCHISLAND Branch.

## <a name="remarks"></a>Comentários
Os valores nesta enumeração são retornados de uma chamada para o [idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
