---
title: IDiaEnumSegments::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a4533b34b35f5050e3bb13a9dee9c74fa69c61d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856345"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Recupera um número especificado de segmentos na sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de segmentos no enumerador a ser recuperado.

 rgelt

fora Uma matriz que deve ser preenchida com os objetos [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) desejados que representam os segmentos.

 pceltFetched

fora Retorna o número de segmentos no enumerador obtido.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver mais segmentos. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)