---
title: CV_access_e | Microsoft Docs
description: Obtenha informações sobre o tipo de enumeração CV_access_e, que especifica o escopo de visibilidade (nível de acesso) de membros no SDK de acesso à interface de depuração.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68dc8ca76e9250cd06009a990c0136912b0d31e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857373"
---
# <a name="cv_access_e"></a>CV_access_e
Especifica o escopo de visibilidade (nível de acesso) de funções e variáveis de membro.

## <a name="syntax"></a>Sintaxe

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementos
CV_private membro tem acesso privado.

CV_protected membro tem acesso protegido.

CV_public membro tem acesso público.

## <a name="remarks"></a>Comentários
O `friend` especificador de acesso não está incluído aqui porque normalmente é usado por funções que não são membros que têm acesso a elementos privados e protegidos da classe. Use o método [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) para localizar símbolos com `SymTagFriend` acesso.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
