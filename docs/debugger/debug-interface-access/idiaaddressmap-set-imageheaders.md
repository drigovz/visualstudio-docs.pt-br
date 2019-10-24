---
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745009"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Define cabeçalhos de imagem para habilitar a conversão de endereço virtual relativa.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parâmetros
 cbData

no Número de bytes de dados de cabeçalho. Deve ser `n*sizeof(IMAGE_SECTION_HEADER)` em que `n` é o número de cabeçalhos de seção no executável.

 data[]

no Uma matriz de estruturas de `IMAGE_SECTION_HEADER` a ser usada como cabeçalhos de imagem.

 originalHeaders

no Defina como `FALSE` se os cabeçalhos de imagem forem da nova imagem, `TRUE` se eles refletirem a imagem original antes de uma atualização. Normalmente, isso seria definido como `TRUE` apenas em combinação com chamadas para o método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A estrutura de `IMAGE_SECTION_HEADER` é declarada em Winnt. h e representa o formato de cabeçalho da seção de imagem do executável.

 Cálculos de endereço virtual relativo dependem dos valores de `IMAGE_SECTION_HEADER`. Normalmente, o DIA recupera esses arquivos do banco de dados do programa (. pdb). Se esses valores estiverem ausentes, o DIA não poderá calcular os endereços virtuais relativos e o método [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) retornará `FALSE`. O cliente deve então chamar o método [IDiaAddressMap::P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) para habilitar os cálculos de endereço virtual relativo depois de fornecer os cabeçalhos de imagem ausentes da própria imagem.

## <a name="see-also"></a>Consulte também
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)