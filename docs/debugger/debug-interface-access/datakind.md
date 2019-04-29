---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21630bea3022769d18748190c2a2d24c0e519a3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554916"
---
# <a name="datakind"></a>DataKind
Indica o escopo específico de um valor de dados.

## <a name="syntax"></a>Sintaxe

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Elementos
Símbolo de DataIsUnknown dados não pode ser determinado.

Item de dados de DataIsLocal é uma variável local.

Item de dados de DataIsStaticLocal é uma variável local estática.

Item de dados de DataIsParam é um parâmetro formal.

Item de dados de DataIsObjectPtr é um ponteiro de objeto (`this`).

Item de dados de DataIsFileStatic é uma variável no escopo do arquivo.

Item de dados de DataIsGlobal é uma variável global.

Item de dados de DataIsMember é uma variável de membro de objeto.

Item de dados de DataIsStaticMember é uma variável de classe estática.

Item de dados DataIsConstant é um valor constante.

## <a name="remarks"></a>Comentários
Os valores nesta enumeração são retornados pelo [idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
