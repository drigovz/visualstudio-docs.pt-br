---
title: IDiaEnumDebugStreams::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::get_Count method
ms.assetid: 5c13fa9a-b35e-47b0-806f-1f53bfe1ba89
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f07b29c1b540a6c89086e51bf633b51114cf62a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856981"
---
# <a name="idiaenumdebugstreamsget_count"></a>IDiaEnumDebugStreams::get_Count
Recupera o número de fluxos de depuração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_Count( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna o número de fluxos de depuração disponíveis neste enumerador.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)