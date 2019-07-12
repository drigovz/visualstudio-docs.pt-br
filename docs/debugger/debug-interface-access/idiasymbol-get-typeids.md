---
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7b32ab5b1965ea7a641cfac470addd2aae0ede0
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64791769"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Recupera uma matriz de valores de identificador de tipo de compilador específicos para esse símbolo.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parâmetros
 `cTypeIds`

[in] Tamanho do buffer para manter os dados.

 `pcTypeIds`

[out] Retorna o número de `typeIds` escrita, ou, se `typeIds` é `NULL`, em seguida, o número total de identificadores de tipo disponíveis.

 `typeIds[]`

[out] Uma matriz que deve ser preenchida com os identificadores de tipo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)