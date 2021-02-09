---
title: IDiaEnumTables::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 739c8e0684e435d4b6747a7127907ec424d90c4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856015"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
Ignora um número especificado de tabelas em uma sequência de enumeração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parâmetros
 `celt`

no O número de tabelas na sequência de enumeração a serem ignoradas.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará `S_FALSE` se não houver mais tabelas a serem ignoradas.

## <a name="see-also"></a>Consulte também
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)