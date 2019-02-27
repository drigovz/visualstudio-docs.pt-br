---
title: IDiaSymbol::get_lowerBound | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBound method
ms.assetid: e9a6440b-d068-4de4-a240-6723d20812b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b85aa6b200707def42cf8eb9a340fee41fcb94f2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611705"
---
# <a name="idiasymbolgetlowerbound"></a>IDiaSymbol::get_lowerBound
Recupera o limite inferior de uma dimensão de matriz FORTRAN.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_lowerBound ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

[out] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o limite inferior de uma dimensão de matriz FORTRAN.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)