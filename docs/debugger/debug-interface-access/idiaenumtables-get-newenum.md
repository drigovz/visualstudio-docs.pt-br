---
title: IDiaEnumTables::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get__NewEnum method
ms.assetid: 7b1159c7-a5f0-4baa-861a-dc11437d8b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07fddc9729063009181e3855a30fd4ee825f14d9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743770"
---
# <a name="idiaenumtablesget__newenum"></a>IDiaEnumTables::get__NewEnum
Recupera a versão <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> deste enumerador.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna a interface de `IUnknown` que representa a versão de <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> deste enumerador.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)