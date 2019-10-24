---
title: IDiaSectionContrib::get_informational | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e425c8bc4e1e3973dac5becc39f3e6c6e9f8dfe8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742643"
---
# <a name="idiasectioncontribget_informational"></a>IDiaSectionContrib::get_informational
Recupera um sinalizador que indica se uma seção contém comentários ou informações semelhantes.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_informational(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retornará `TRUE` se a seção contiver comentários ou outras informações; caso contrário, retorna `FALSE`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, a seção. diretivo contém informações.

## <a name="see-also"></a>Consulte também
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)