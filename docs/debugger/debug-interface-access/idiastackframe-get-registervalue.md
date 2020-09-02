---
title: 'IDiaStackFrame:: get_registerValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42bd724e4f25b5475f89af32f5793ede8d66594a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464964"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Recupera o valor de um registro especificado como armazenado no quadro de pilha.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `registerIndex`

no Um dos valores de enumeração de [enumeração de CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) .

 `pRetVal`

fora Valor armazenado no registro.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.

## <a name="see-also"></a>Confira também
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [Enumeração CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)