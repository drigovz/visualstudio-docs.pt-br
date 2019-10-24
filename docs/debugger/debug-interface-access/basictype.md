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
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745484"
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
btNoType nenhum tipo básico foi especificado.

o tipo básico btVoid é um `void`.

o tipo básico btChar é um `char` (CC++ /Type).

o tipo básico btWChar é um caractere (Unicode) largo (`WCHAR`).

o tipo básico btInt é `signed int` (CC++ /Type).

o tipo básico btUInt é `unsigned int` (CC++ /Type).

o tipo básico btFloat é um número de ponto flutuante (`FLOAT`).

o tipo básico btBCD é um decimal codificado em binário (`BCD`).

o tipo básico btBool é um booliano (`BOOL`).

o tipo básico btLong é um `long int` (CC++ /Type).

o tipo básico btULong é um `unsigned long int` (CC++ /Type).

o tipo básico do btCurrency é Currency.

o tipo básico btDate é data/hora (`DATE`).

o tipo básico btVariant é uma estrutura de tipo de variável (`VARIANT`).

o tipo básico btComplex é um número complexo.

o tipo básico do btBit é um pouco.

o tipo básico btBSTR é uma cadeia de caracteres básica ou binária (`BSTR`).

o tipo básico btHresult é um `HRESULT`.

## <a name="remarks"></a>Comentários
Os valores nessa enumeração são retornados pelo método [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
