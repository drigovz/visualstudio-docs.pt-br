---
title: IDiaEnumFrameData::frameByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5aa30598dcae08842c935d0d404cbb8b3303aefe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856876"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
Retorna um quadro pelo endereço virtual relativo (RVA).

## <a name="syntax"></a>Sintaxe

```C++
HRESULT frameByRVA( 
   DWORD           relativeVirtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Parâmetros
 relativeVirtualAddress

no RVA do quadro de interesse.

 frame

fora Retorna um objeto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que representa o quadro que contém o endereço fornecido.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se nenhum dado de quadro corresponder ao endereço especificado. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)