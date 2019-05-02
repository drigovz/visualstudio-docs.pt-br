---
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54e573cde9b2317be39f18e3953ebeaedf2717e3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400835"
---
# <a name="idiasymbolgettargetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Recupera o endereço virtual relativo (RVA) de um destino da conversão.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_targetRelativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

[out] Retorna o RVA de um destino da conversão.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="remarks"></a>Comentários
 Essa propriedade é válida somente se o símbolo como um [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valor `SymTagThunk`.

 Uma "conversão" é um trecho de código que converte entre um espaço de endereço de memória de 32 bits (também conhecido como o espaço de endereço simples) e um espaço de endereço de 16 bits (conhecido como um espaço de endereçamento segmentado).

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)