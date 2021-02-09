---
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c753811378ee81deb5d0deacb8035c1768e80c50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856470"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Recupera contribuições de seção por meio de um índice.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>Parâmetros
 índice

no Índice do objeto [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) a ser recuperado. O índice está no intervalo de 0 a `count` -1, em que `count` é retornado pelo método [IDiaEnumSectionContribs:: get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) .

 section

fora Retorna um objeto [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) que representa a contribuição da seção desejada.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)