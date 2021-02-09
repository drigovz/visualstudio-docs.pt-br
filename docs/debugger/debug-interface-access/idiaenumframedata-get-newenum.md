---
title: IDiaEnumFrameData::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::get__NewEnum method
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f47c7bd33c04f80909a6ab1732246e4e31dedf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856820"
---
# <a name="idiaenumframedataget__newenum"></a>IDiaEnumFrameData::get__NewEnum
Recupera a <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versão deste enumerador.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 pRetVal

fora Retorna a `IUnknown` interface que representa a <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versão deste enumerador.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)