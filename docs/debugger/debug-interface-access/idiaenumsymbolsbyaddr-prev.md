---
title: IDiaEnumSymbolsByAddr::Prev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a1b69dbd7e502340e7d563523288a095b733c2d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619414"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Recupera os símbolos anteriores na ordem pelo endereço.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Prev ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parâmetros
 celt

[in] O número de símbolos no enumerador a ser recuperado.

 rgelt

[out] Uma matriz que deve ser preenchida com [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representam os símbolos desejados.

 pceltFetched

[out] Retorna o número de símbolos no enumerador buscado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum símbolo anterior. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método atualiza a posição de enumerador pelo número de elementos buscada.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)