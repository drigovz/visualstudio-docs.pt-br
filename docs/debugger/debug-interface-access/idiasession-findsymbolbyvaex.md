---
title: IDiaSession::findSymbolByVAEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVAEx method
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16b62c5efb520e90606d6311b60a839404359720
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832357"
---
# <a name="idiasessionfindsymbolbyvaex"></a>IDiaSession::findSymbolByVAEx
Recupera um tipo de símbolo especificado que contém ou está mais próximo de um endereço virtual especificado (VA) e o deslocamento.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findSymbolByVAEx ( 
   ULONGLONG    va,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>Parâmetros
 `va`

[in] Especifica a VA.

 `symtag`

[in] Tipo de símbolo a ser localizada. Valores são tirados de [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração.

 `ppSymbol`

[out] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperado do objeto que representa o símbolo.

 `displacement`

[out] Retorna um valor que especifica um deslocamento de endereço virtual fornecido pelo `va`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="example"></a>Exemplo

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>Consulte também
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)