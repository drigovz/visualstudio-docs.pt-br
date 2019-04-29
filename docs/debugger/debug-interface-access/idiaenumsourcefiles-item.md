---
title: IDiaEnumSourceFiles::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 403aa09a487ea1587ab30389f180afecec5ac6bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833331"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Recupera um arquivo de origem por meio de um índice.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Parâmetros
 índice

[in] Índice do [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto a ser recuperado. O índice está no intervalo de 0 a `count`-1, onde `count` é retornado pelo [idiaenumsourcefiles:: Get_count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) método.

 sourceFile

[out] Retorna um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto que representa o arquivo de origem desejado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)