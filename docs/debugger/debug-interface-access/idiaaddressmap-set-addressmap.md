---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745024"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Fornece um mapa de endereços para dar suporte a traduções de layout de imagem.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Parâmetros
 `cbData`

no O número de elementos no parâmetro `data`.

 `data[]`

no Uma matriz de estruturas de [estrutura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) que definem o mapa de tradução.

 `imagetoSymbols`

[in] `TRUE` se o parâmetro `data` define um mapa do layout da nova imagem para o layout original (conforme descrito pelos símbolos de depuração). `FALSE` se `data` é um mapa para o novo layout de imagem obtido do layout original.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, o DIA recupera mapas de conversão de endereços do arquivo de banco de dados do programa (. pdb). Se esses valores estiverem ausentes, o método [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) será chamado duas vezes, uma vez com o parâmetro `imagetoSymbols` definido como `TRUE` e uma vez com o parâmetro `imagetoSymbols` definido como `FALSE`. As traduções do mapa de endereços não podem ser habilitadas usando o método [IDiaAddressMap::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , a menos que ambos os mapas de tradução sejam fornecidos.

## <a name="see-also"></a>Consulte também
- [Estrutura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)