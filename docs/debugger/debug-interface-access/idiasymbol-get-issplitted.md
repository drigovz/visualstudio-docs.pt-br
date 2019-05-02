---
title: IDiaSymbol::get_isSplitted | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee91134997dad5f5361de6b07af1a99dfc420f5e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401234"
---
# <a name="idiasymbolgetissplitted"></a>IDiaSymbol::get_isSplitted
Recupera um sinalizador que especifica se o símbolo de dados foi dividido em uma agregação ou uma coleção de outros símbolos; o compilador trata os símbolos como entidades separadas, mesmo que eles realmente fazem parte de um símbolo de maior.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parâmetros
 `pFlag`

[out] Retorna `TRUE` se o símbolo foi dividido em uma agregação de símbolos; caso contrário, retornará `FALSE`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou código de erro.

> [!NOTE]
> Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="remarks"></a>Comentários
 O [idiasymbol:: Get_isaggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) retorno do método `TRUE` para todos os símbolos que fazem parte de um símbolo de divisão.

## <a name="requirements"></a>Requisitos

|Requisito|Descrição|
|-----------------|-----------------|
|Cabeçalho:|dia2.h|
|Versão:|V DIA SDK 8.0|

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)