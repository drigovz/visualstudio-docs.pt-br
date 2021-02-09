---
title: IDiaEnumDebugStreams::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8a0ce0ecb65d18c3c5a3c4e11bbcf80171c25ac2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856904"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
Ignora um número especificado de fluxos de depuração em uma sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parâmetros
 `celt`

no O número de fluxos de depuração na sequência de enumeração a serem ignorados.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará `S_FALSE` se não houver mais registros a serem ignorados.

## <a name="see-also"></a>Consulte também
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)