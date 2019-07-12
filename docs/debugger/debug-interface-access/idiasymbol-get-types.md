---
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19642e6875e81220cb20109ce45e8dca40777a63
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786565"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Recupera uma matriz de tipos específicos do compilador para esse símbolo.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parâmetros
 `cTypes`

[in] Tamanho do buffer para manter os dados.

 `pcTypes`

[out] Retorna o número de tipos escritos, ou, se o `types` parâmetro é `NULL`, em seguida, o número total de tipos disponíveis.

 `types[]`

[out] Uma matriz que deve ser preenchido com o [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representam todos os tipos para esse símbolo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)