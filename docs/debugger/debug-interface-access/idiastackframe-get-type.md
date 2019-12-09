---
title: IDiaStackFrame::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_type method
ms.assetid: 99daa97b-5c05-455d-bd1e-800762ccf7c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9a2a433c33d46215168238e9956ce0427171b24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741564"
---
# <a name="idiastackframeget_type"></a>IDiaStackFrame::get_type
Recupera o tipo de quadro.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna um valor da enumeração de [Enumeração StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) .

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se a propriedade não tiver suporte. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [Enumeração StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)