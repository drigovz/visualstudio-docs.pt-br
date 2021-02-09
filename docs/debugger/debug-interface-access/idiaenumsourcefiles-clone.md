---
title: IDiaEnumSourceFiles::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6a8c87a0dd4606396249409984cb0589991cc6c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856316"
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Clone ( 
   IDiaEnumSourceFiles** ppenum
);
```

#### <a name="parameters"></a>Parâmetros
 ppenum

fora Retorna um objeto [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) que contém uma duplicata do enumerador. Os arquivos de origem não são duplicados, somente o enumerador.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)