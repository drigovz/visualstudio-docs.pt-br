---
title: IDiaEnumDebugStreams::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68a4925a8df181106d1aa902ce89462253a8d16f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857009"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreams** ppenum
);
```

#### <a name="parameters"></a>Parâmetros
 `ppenum`

fora Retorna um objeto [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) que contém uma duplicata do enumerador. Os fluxos não são duplicados, somente o enumerador.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)