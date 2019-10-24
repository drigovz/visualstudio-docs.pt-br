---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738643"
---
# <a name="locationtype"></a>LocationType
Indica o tipo de informações de local contidas em um símbolo.

## <a name="syntax"></a>Sintaxe

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Elementos
`LocIsNull` informações de local não estão disponíveis.

`LocIsStatic` local é estático.

`LocIsTLS` local está no armazenamento local de thread.

o local do `LocIsRegRel` é relativo ao registro.

`LocIsThisRel` local é `this`-relativo.

`LocIsEnregistered` local está em um registro.

`LocIsBitField` local está em um campo de bits.

`LocIsSlot` local é um slot MSIL (Microsoft Intermediate Language).

`LocIsIlRel` local é MSIL-Relative.

o local do `LocInMetaData` está nos metadados.

`LocIsConstant` local está em um valor constante.

`LocTypeMax` o número de tipos de localização nesta enumeração.

## <a name="remarks"></a>Comentários
As propriedades disponíveis para a interface [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dependem do local do símbolo dentro do arquivo de imagem. Para obter mais informações, consulte [locais de símbolo](../../debugger/debug-interface-access/symbol-locations.md).

Os valores nessa enumeração são retornados por uma chamada para o método [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)
