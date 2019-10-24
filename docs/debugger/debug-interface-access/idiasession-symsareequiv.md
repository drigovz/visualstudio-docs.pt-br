---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741864"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Verifica se dois símbolos são equivalentes.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parâmetros
 `symbolA`

no O primeiro objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) usado na comparação.

 `symbolB`

no O segundo objeto `IDiaSymbol` usado na comparação.

## <a name="return-value"></a>Valor retornado
 Se os símbolos forem equivalentes, retornará `S_OK`; caso contrário, retorna `S_FALSE`, os símbolos não são equivalentes. Caso contrário, retorne um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)