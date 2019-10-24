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
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745260"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Descreve uma entrada em um mapa de endereços.

## <a name="syntax"></a>Sintaxe

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementos
`rva` um endereço virtual relativo (RVA) na imagem A.

`rvaTo` o endereço virtual relativo `rva` está mapeado para a imagem B.

## <a name="remarks"></a>Comentários
Um mapa de endereços fornece uma tradução de um layout de imagem (A) para outro (B). Uma matriz de estruturas de `DiaAddressMapEntry` classificadas por `rva` define um mapa de endereços.

Para converter um endereço, `addrA`, na imagem A para um endereço, `addrB`, na imagem B, execute as seguintes etapas:

1. Pesquise o mapa para obter a entrada, `e`, com o maior `rva` menor ou igual a `addrA`.

2. Defina `delta = addrA - e.rva`.

3. Defina `addrB = e.rvaTo + delta`.

    Uma matriz de estruturas de `DiaAddressMapEntry` é passada para o método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: dia2. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
