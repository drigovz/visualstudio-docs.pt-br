---
title: IDiaSectionContrib::get_nopad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a81113242379070e56d6d0bd0f916355985eaa42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742619"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
Recupera um sinalizador que indica se a seção não deve ser preenchida para o próximo limite de memória.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna `TRUE` se a seção não deve ser preenchida para o próximo limite de memória; caso contrário, retorna `FALSE`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Essa é uma propriedade normalmente vista apenas em arquivos mais antigos.

## <a name="see-also"></a>Consulte também
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)