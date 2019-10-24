---
title: IDiaSession::findSymbolByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVA method
ms.assetid: 0350df23-9a5d-4e8d-8c26-7f571d8fb1af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf73c47234bb680ee107a2703e77b9259fb00040
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742009"
---
# <a name="idiasessionfindsymbolbyva"></a>IDiaSession::findSymbolByVA
Recupera um tipo de símbolo especificado que contém ou está mais próximo de um endereço virtual especificado.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findSymbolByVA ( 
   ULONGLONG    va,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parâmetros
 `va`

no Especifica o endereço virtual.

 `symtag`

no Tipo de símbolo a ser encontrado. Os valores são obtidos da enumeração de [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .

 `ppSymbol`

fora Retorna um objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o símbolo recuperado.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="example"></a>Exemplo

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByVA( va, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>Consulte também
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)