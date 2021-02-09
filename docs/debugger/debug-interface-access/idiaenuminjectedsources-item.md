---
title: IDiaEnumInjectedSources::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 029c47cc04a09dc1168ff755c1640da9c9662207
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856708"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Recupera uma fonte injetada por meio de um índice.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>Parâmetros
 índice

no Índice do objeto [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) a ser recuperado. O índice é o intervalo de 0 a `count` -1, em que `count` é retornado pelo método [IDiaEnumInjectedSources:: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) .

 injectedSource

fora Retorna um objeto [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) que representa a fonte injetada.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)