---
title: IDiaSession::symbolById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0ffcb6c438150bff82f17a66c3347c300b17d72
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741874"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Recupera um símbolo por seu identificador exclusivo.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parâmetros
`id`

no Identificador exclusivo.

`ppSymbol`

fora Retorna um objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o símbolo recuperado.

## <a name="return-value"></a>Valor retornado
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
O identificador especificado é um valor exclusivo usado internamente pelo DIA SDK para tornar todos os símbolos exclusivos.

Esse método pode ser usado, por exemplo, para recuperar o símbolo que representa o tipo de outro símbolo (consulte o exemplo).

## <a name="example"></a>Exemplo
Este exemplo recupera um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o tipo de outro símbolo. Este exemplo mostra como usar o método `symbolById` na sessão. Uma abordagem mais simples é chamar o método [IDiaSymbol:: get_Type](../../debugger/debug-interface-access/idiasymbol-get-type.md) para recuperar o símbolo de tipo diretamente.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Consulte também
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
