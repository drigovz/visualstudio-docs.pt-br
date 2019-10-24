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
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738503"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Designa tipos de conversão.

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
Conversão padrão de THUNK_ORDINAL_NOTYPE.

THUNK_ORDINAL_ADJUSTOR uma conversão de `this` do ajustador.

Conversão de chamada virtual THUNK_ORDINAL_VCALL.

THUNK_ORDINAL_PCODE P-conversão de código.

Conversão de carga de atraso THUNK_ORDINAL_LOAD.

Conversão incremental de trampoline THUNK_ORDINAL_TRAMP_INCREMENTAL (uma conversão trampoline é usada para chamar chamadas de um espaço de memória para outro).

Trampoline conversão do ponto de ramificação THUNK_ORDINAL_TRAMP_BRANCHISLAND.

## <a name="remarks"></a>Comentários
Os valores nessa enumeração são retornados de uma chamada para o método [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
