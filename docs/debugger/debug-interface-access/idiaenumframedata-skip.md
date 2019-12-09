---
title: IDiaEnumFrameData::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c49aaf1f648a52e1701088b6579eda55cde6c355
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744567"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Ignora um número especificado de elementos de dados de quadro em uma sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parâmetros
 celt

no O número de elementos de dados de quadro na sequência de enumeração a serem ignorados.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará `S_FALSE` se não houver mais registros a serem ignorados.

## <a name="see-also"></a>Consulte também
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)