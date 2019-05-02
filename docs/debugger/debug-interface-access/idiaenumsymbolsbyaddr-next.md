---
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52567eddcbb6c4f372256e66b7b723bc7aa7394
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833435"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Recupera os símbolos Avançar na ordem pelo endereço.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parâmetros
 celt

[in] O número de símbolos no enumerador a ser recuperado.

 rgelt

[out] Uma matriz que deve ser preenchido com o [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representam os símbolos desejados.

 pceltFetched

[out] Retorna o número de símbolos no enumerador buscado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum símbolo de mais. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método atualiza a posição de enumerador pelo número de elementos buscada.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)