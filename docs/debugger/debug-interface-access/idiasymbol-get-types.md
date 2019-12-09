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
ms.openlocfilehash: 6d23ea3c4d885b3f7575c998999814d0808d03bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739063"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Recupera uma matriz de tipos específicos do compilador para este símbolo.

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

no Tamanho do buffer para armazenar os dados.

 `pcTypes`

fora Retorna o número de tipos gravados ou, se o parâmetro `types` for `NULL`, o número total de tipos disponíveis.

 `types[]`

fora Uma matriz que deve ser preenchida com os objetos [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representam todos os tipos desse símbolo.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)