---
title: IDiaEnumInjectedSources::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Skip method
ms.assetid: 4aad6a51-f2d3-4064-b216-60d830d0a560
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab2adf44fa1ed2d394a6ad5edaca0818c503a180
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856659"
---
# <a name="idiaenuminjectedsourcesskip"></a>IDiaEnumInjectedSources::Skip
Ignora um número especificado de fontes injetadas em uma sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de fontes injetadas na sequência de enumeração a serem ignoradas.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará se não houver `S_FALSE` mais fontes injetadas para ignorar.

## <a name="see-also"></a>Consulte também
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)