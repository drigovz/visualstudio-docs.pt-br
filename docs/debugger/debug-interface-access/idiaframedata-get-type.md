---
title: IDiaFrameData::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76696529440d6ecce34f623c51e2909d0b2d7f00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855882"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
Recupera o tipo de quadro específico do compilador.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna um valor da enumeração de [Enumeração StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) que indica o tipo de quadro específico do compilador.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Enumeração StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)