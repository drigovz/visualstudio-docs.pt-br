---
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31cff55617e21c8ed750800fec982f2b1492d977
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862566"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Recupera uma matriz de valores de identificador de tipo específicos do compilador para este símbolo.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parâmetros
 `cTypeIds`

no Tamanho do buffer para armazenar os dados.

 `pcTypeIds`

fora Retorna o número de `typeIds` gravados ou, se `typeIds` for `NULL` , o número total de identificadores de tipo disponíveis.

 `typeIds[]`

fora Uma matriz que deve ser preenchida com os identificadores de tipo.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)