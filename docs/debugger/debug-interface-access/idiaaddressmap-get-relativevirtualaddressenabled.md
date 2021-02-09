---
title: IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 58d7bc241ed2e0fc885ace301b611918d1822dac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857198"
---
# <a name="idiaaddressmapget_relativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Indica se o cálculo e o uso de endereços virtuais relativos (RVA) estão habilitados.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 pRetVal

fora Retorna `TRUE` se o cálculo de RVAs está habilitado.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 RVAs serão habilitados se os segmentos tiverem sido inicialmente carregados de um arquivo PDB. O uso de RVAs pode ser temporariamente desabilitado chamando o método [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) .

 Além disso, novos cabeçalhos de imagem podem ser estabelecidos chamando o método [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) seguido por uma chamada para o `put_relativeVirtualAddressEnabled` método para habilitar o uso de RVAs usando os novos cabeçalhos de imagem.

## <a name="see-also"></a>Consulte também
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)