---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742305"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Retorna uma enumeração de símbolos para quadros embutidos correspondentes ao nome da função embutida especificada.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parâmetros
 `name`

no O nome da função embutida a ser pesquisada.

 `option`

no As opções de pesquisa de nome a serem usadas ao pesquisar quadros embutidos que correspondam a `name`. Para obter mais informações, consulte [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

fora Um ponteiro para um ponteiro de interface `IDiaEnumSymbols` que é inicializado com o resultado.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Essa função procura Inlines apenas nas funções de stub do acelerador. Ele ignora os registros C++ de procedimento nativo.

## <a name="see-also"></a>Consulte também
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)