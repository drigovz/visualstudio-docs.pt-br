---
title: IDiaEnumFrameData::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6a0d7a98884d217bb8172d53768917e8e8f7453d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856792"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Recupera um número especificado de elementos de dados de quadro na sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de elementos de dados de quadro no enumerador a ser recuperado.

 rgelt

fora Uma matriz de objetos [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) a ser preenchida com os elementos de dados de quadro solicitados.

 pceltFetched

fora Retorna o número de elementos de dados de quadro no enumerador obtido.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver mais registros. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)