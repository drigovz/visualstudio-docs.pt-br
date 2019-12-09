---
title: 'IDiaStackFrame:: get_functionStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_functionStart
ms.assetid: e3e6e88b-0594-4d82-9457-480239a2e85a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9900b6301388479fc71f1b257113974056aeb3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741719"
---
# <a name="idiastackframeget_functionstart"></a>IDiaStackFrame::get_functionStart
Recupera um sinalizador que indica se o bloco contém o ponto de entrada de uma função.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna `TRUE` se o registro de ativação contiver o ponto de entrada de uma função; caso contrário, retorna `FALSE`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se a propriedade não tiver suporte. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)