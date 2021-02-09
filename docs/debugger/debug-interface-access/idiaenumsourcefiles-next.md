---
title: IDiaEnumSourceFiles::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e33abf7a38c5acab799b8a9f9342b2002d62a21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856232"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
Recupera um número especificado de arquivos de origem na sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaSourceFile** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de arquivos de origem no enumerador a ser recuperado.

 rgelt

fora Uma matriz que deve ser preenchida com os objetos [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) que representam os arquivos de origem desejados.

 pceltFetched

fora Retorna o número de arquivos de origem no enumerador obtido.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver mais arquivos de origem. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)