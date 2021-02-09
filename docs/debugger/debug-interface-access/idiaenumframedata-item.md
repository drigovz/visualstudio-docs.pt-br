---
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d8d2335cf84ece792b710725156d2f74e3f33770
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856813"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Recupera um elemento de dados de quadro por meio de um índice.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Parâmetros
 índice

no Índice do objeto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) a ser recuperado. O índice está no intervalo de 0 a `count` -1, em que `count` é retornado pelo método [IDiaEnumFrameData:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .

 section

fora Retorna um objeto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que representa o elemento de dados de quadro desejado.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)