---
title: IDiaEnumSourceFiles::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8474899ac5f1a0617bc0adfc110dbb773d6b6b43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856197"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
Ignora um número especificado de arquivos de origem em uma sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de arquivos de origem na sequência de enumeração a serem ignorados.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará `S_FALSE` se não houver mais arquivos de origem a serem ignorados.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)