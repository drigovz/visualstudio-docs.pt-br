---
title: BasicType | Microsoft Docs
description: Encontre informações de referência sobre a enumeração BasicType, que especifica o tipo básico de um símbolo no SDK de acesso à interface de depuração do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a86a25d02b1aa51e49d80b71dbd37b2aa4c2d103
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865585"
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

o tipo básico de btVoid é um `void` .

o tipo básico de btChar é um `char` (tipo C/C++).

o tipo básico btWChar é um caractere (Unicode) largo ( `WCHAR` ).

o tipo básico btInt é `signed int` (tipo C/C++).

o tipo básico btUInt é `unsigned int` (tipo C/C++).

o tipo básico btFloat é um número de ponto flutuante ( `FLOAT` ).

o tipo básico btBCD é um decimal codificado em binário ( `BCD` ).

o tipo básico btBool é um booliano ( `BOOL` ).

o tipo básico de btLong é um `long int` (tipo C/C++).

o tipo básico btULong é um `unsigned long int` (tipo C/C++).

o tipo básico do btCurrency é Currency.

o tipo básico btDate é Date/Time ( `DATE` ).

o tipo básico btVariant é uma estrutura de tipo de variável ( `VARIANT` ).

o tipo básico btComplex é um número complexo.

o tipo básico do btBit é um pouco.

o tipo básico btBSTR é uma cadeia de caracteres básica ou binária ( `BSTR` ).

o tipo básico de btHresult é um `HRESULT` .

## <a name="remarks"></a>Comentários
Os valores nessa enumeração são retornados pelo método [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Confira também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
