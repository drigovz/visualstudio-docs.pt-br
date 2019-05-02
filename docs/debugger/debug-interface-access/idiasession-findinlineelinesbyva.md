---
title: IDiaSession::findInlineeLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58f572fcce0b490fad8f94f1e3e3d941e8568211
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827726"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Recupera uma enumeração que permite que um cliente iterar por meio das informações de número de linha de todas as funções que são embutidas, diretamente ou indiretamente, pelo símbolo pai especificado e está contida dentro do endereço virtual especificado (VA).

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parâmetros
 `parent`

[in] Um `IDiaSymbol` que representa o pai do objeto.

 `va`

[in] Especifica o endereço como um VA.

 `length`

[in] Especifica o intervalo de endereços, no número de bytes, para cobrir com essa consulta.

 `ppResult`

[out] Mantém um `IDiaEnumLineNumbers` objeto que contém a lista de números de linha são recuperadas.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)