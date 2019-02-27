---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b768b06e0702f7929b402086dcc6e11918f3e683
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630087"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Define o endereço de carregamento para o arquivo executável que corresponde aos símbolos nesse repositório de símbolos.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parâmetros
 `NewVal`

[in] Carregar o endereço para o arquivo executável.

## <a name="remarks"></a>Comentários
 Propriedades de endereço virtual (VA) de símbolo são calculadas usando o valor desse método. Endereços virtuais não são calculados, a menos que essa propriedade é definida como diferente de zero.

> [!NOTE]
>  Você deve chamar esse método quando você receber o [IDiaSession](../../debugger/debug-interface-access/idiasession.md) do objeto e antes de começar a usar o objeto se você precisar usar quaisquer propriedades virtuais nos símbolos.

## <a name="see-also"></a>Consulte também
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)