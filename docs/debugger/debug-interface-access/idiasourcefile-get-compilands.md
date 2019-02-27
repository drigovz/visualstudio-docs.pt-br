---
title: 'Idiasourcefile:: Get_compilands | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15ebc8296bdf78515b31d38a7543a4f41db84664
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613018"
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
Recupera um enumerador de compilandos que têm números de linha, fazendo referência a esse arquivo.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_compilands ( 
   IDiaEnumSymbols** ppRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `ppRetVal`

[out] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) objeto que contém uma lista de compilandos todos os que têm números de linha, fazendo referência a esse arquivo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)