---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c63d38e1b4d79227cfdc694dc6d8c154a01532f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853208"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Especifica as opções de pesquisa para nomes de arquivo e símbolo.

## <a name="syntax"></a>Sintaxe

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Elementos
`nsNone` Nenhuma opção foi especificada.

`nsfCaseSensitive` Aplica uma correspondência de nome que diferencia maiúsculas de minúsculas.

`nsfCaseInsensitive` Aplica uma correspondência de nome que não diferencia maiúsculas de minúsculas.

`nsfFNameExt` Trata os nomes como caminhos e aplica uma correspondência de nome filename. ext.

`nsfRegularExpression` Aplica uma correspondência de nome que diferencia maiúsculas de minúsculas usando asteriscos (*) e pontos de interrogação (?) como curingas. (Não há suporte para outros caracteres comuns de expressão regular.)

`nsfUndecoratedName` Aplica-se somente a símbolos que têm nomes não decorados e decorados.

## <a name="remarks"></a>Comentários
Os valores dessa enumeração são passados para os seguintes métodos:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: dia2. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
