---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626109"
---
# <a name="basictype"></a>BasicType
Especifica o tipo básico do símbolo.

## <a name="syntax"></a>Sintaxe

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Elementos
btNoType que nenhum tipo básico é especificado.

btVoid tipo básico é um `void`.

btChar tipo básico é um `char` (tipo de C/C++).

btWChar tipo básico é um caractere largo de (Unicode) (`WCHAR`).

btInt tipo básico é `signed int` (tipo de C/C++).

btUInt tipo básico é `unsigned int` (tipo de C/C++).

btFloat tipo básico é um número de ponto flutuante (`FLOAT`).

btBCD tipo básico é um decimal codificado binário (`BCD`).

btBool tipo básico é um valor booliano (`BOOL`).

btLong tipo básico é um `long int` (tipo de C/C++).

btULong tipo básico é um `unsigned long int` (tipo de C/C++).

btCurrency tipo básico é a moeda.

btDate tipo básico é data/hora (`DATE`).

btVariant tipo básico é uma estrutura de tipo de variável (`VARIANT`).

btComplex tipo básico é um número complexo.

btBit tipo básico é um pouco.

btBSTR tipo básico é uma cadeia de caracteres básica ou binary (`BSTR`).

btHresult tipo básico é um `HRESULT`.

## <a name="remarks"></a>Comentários
Os valores nesta enumeração são retornados pelo [idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
