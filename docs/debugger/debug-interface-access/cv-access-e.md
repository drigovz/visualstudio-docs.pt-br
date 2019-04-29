---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90230bd95e1dbcd3e4c186257c6c36faad6ba1f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555124"
---
# <a name="cvaccesse"></a>CV_access_e
Especifica o escopo de visibilidade (nível de acesso) de funções de membro e variáveis.

## <a name="syntax"></a>Sintaxe

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementos
Membro de CV_private tem acesso privado.

Membro de CV_protected tenha acesso protegido.

Membro de CV_public tem acesso público.

## <a name="remarks"></a>Comentários
O `friend` especificador de acesso não é incluída aqui porque ele é normalmente usado por funções não membro que têm acesso a elementos particulares e protegidos da classe. Use o [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método para localizar símbolos com `SymTagFriend` acesso.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
