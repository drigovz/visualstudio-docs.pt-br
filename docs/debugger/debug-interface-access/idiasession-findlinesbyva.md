---
title: IDiaSession::findLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2513825fd2b6f4e6035f9f23295f0c9f00385d0a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742070"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Recupera as informações de número de linha para as linhas contidas em um intervalo de endereço virtual (VA) especificado.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parâmetros
`va`

no Especifica o endereço como um VA.

`length`

no Especifica o número de bytes de intervalo de endereços a serem abordados com essa consulta.

`ppResult`

fora Retorna um objeto [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) que contém uma lista de todos os números de linha que abrangem o intervalo de endereços especificado.

## <a name="example"></a>Exemplo
Este exemplo mostra uma função que obtém todos os números de linha contidos em uma função usando o comprimento e o endereço virtual da função.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Consulte também
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
