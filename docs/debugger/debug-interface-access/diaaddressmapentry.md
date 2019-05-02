---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 311762f4eafc8dad63da5854870f2836ee68b3ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554890"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Descreve uma entrada em um mapa de endereço.

## <a name="syntax"></a>Sintaxe

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementos
`rva` Um endereço virtual relativo (RVA) na imagem A.

`rvaTo` O endereço virtual relativo `rva` é mapeado para imagem B.

## <a name="remarks"></a>Comentários
Um mapa de endereço fornece uma tradução do layout de uma imagem (A) para outro (B). Uma matriz de `DiaAddressMapEntry` estruturas classificadas por `rva` define um mapa de endereço.

Para converter um endereço `addrA`, na imagem de um para um endereço, `addrB`, na imagem B, execute as seguintes etapas:

1. O mapa para a entrada de pesquisa `e`, com o maior `rva` menor ou igual a `addrA`.

2. Defina `delta = addrA - e.rva`.

3. Defina `addrB = e.rvaTo + delta`.

    Uma matriz de `DiaAddressMapEntry` estruturas é passada para o [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: dia2.h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
