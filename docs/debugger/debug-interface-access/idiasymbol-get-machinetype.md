---
title: IDiaSymbol::get_machineType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29bdfbab41c5382661e022d38a190d3bd19c38c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462913"
---
# <a name="idiasymbolget_machinetype"></a>IDiaSymbol::get_machineType
Recupera o tipo da CPU de destino.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_machineType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna um valor das [constantes IMAGE_FILE_MACHINE_](/windows/desktop/SysInfo/image-file-machine-constants) que especifica o tipo de CPU de destino.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="see-also"></a>Confira também
- [IMAGE_FILE_MACHINE_ constantes](/windows/desktop/SysInfo/image-file-machine-constants) 
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)