---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45ed43bf65c38890ca7ebda1a6b1719532697eae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738452"
---
# <a name="udtkind"></a>UdtKind
Descreve a variedade de UDT (tipo definido pelo usuário).

## <a name="syntax"></a>Sintaxe

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Elementos
UdtStruct UDT é uma estrutura.

UdtClass UDT é uma classe.

UdtUnion UDT é uma União.

UdtInterface UDT é uma interface.

## <a name="remarks"></a>Comentários
Os valores nessa enumeração são retornados pelo método [IDiaSymbol:: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
