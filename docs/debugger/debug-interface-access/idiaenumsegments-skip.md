---
title: IDiaEnumSegments::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efedd0e24c96259f1c9e9b6fc7522ee250bd4b25
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744164"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Ignora um número especificado de segmentos em uma sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de segmentos na sequência de enumeração a serem ignorados.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará `S_FALSE` se não houver mais segmentos a serem ignorados.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)