---
title: IDiaEnumDebugStreams::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f70b052746438516275b205676339b216eea70e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856960"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
Recupera um número especificado de fluxos de depuração na sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Next ( 
   ULONG                     celt,
   IDiaEnumDebugStreamData** rgelt,
   ULONG*                    pceltFetched
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de fluxos de depuração no enumerador a serem recuperados.

 rgelt

fora Retorna uma matriz de objetos [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) que representa os fluxos de depuração que estão sendo recuperados.

 pceltFetched

fora Retorna o número de fluxos de depuração retornados.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver mais fluxos. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)