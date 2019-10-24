---
title: IDiaSymbol::get_intro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4680af2d41ef3fa06a89784003c98982a09c2b63
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740345"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Recupera um sinalizador que especifica se a função é uma função virtual de introdução.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
`pRetVal`

fora Retorna `TRUE` se a função for de introdução virtual; caso contrário, retorna `FALSE`.

## <a name="return-value"></a>Valor retornado
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou código de erro.

> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="example"></a>Exemplo

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Tanto `A::f1` quanto `B::f1` são funções virtuais, mas `A::f1` é a introdução virtual.

## <a name="requirements"></a>Requisitos

|Requisito|Descrição|
|-----------------|-----------------|
|Cabeçalho:|dia2.h|
|Versão:|DIA SDK v 7.0|

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
