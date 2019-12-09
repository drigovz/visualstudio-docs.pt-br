---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743443"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Recupera o local da memória onde a imagem deve ser baseada.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna o valor base da imagem sugerida.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Devido a conflitos na base da imagem, uma imagem pode ser reutilizada automaticamente para um local de memória não utilizado quando ela é carregada. Esse método retorna a dica de base (local da memória sugerida) que foi armazenada no módulo no momento da compilação.

## <a name="see-also"></a>Consulte também
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)