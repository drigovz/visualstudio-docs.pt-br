---
title: 'IDiaStackFrame:: get_size | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_size method
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04fec0f24cd8d905b41e8eb142ab3f1f37023860
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741593"
---
# <a name="idiastackframeget_size"></a>IDiaStackFrame::get_size
Recupera o tamanho do quadro de pilha em bytes.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_size ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna o tamanho do quadro de pilha em bytes.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se a propriedade não tiver suporte. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)