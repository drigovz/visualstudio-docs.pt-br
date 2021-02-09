---
title: IDiaEnumSymbols::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d3ee009805fba0d3a0d8a36477072121e594c4ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856134"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Recupera um símbolo por meio de um índice.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>Parâmetros
 índice

no Índice do objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) a ser recuperado. O índice está no intervalo de 0 a `count` -1, em que `count` é retornado pelo método [IDiaEnumSymbols:: get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) .

 símbolo

fora Retorna um objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o símbolo desejado.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)