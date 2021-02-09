---
title: IDiaAddressMap::get_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09d4507df7090e36f9436f2ca24b6f982d56f420
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857226"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indica se um mapa de endereço foi estabelecido para uma sessão específica.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 pRetVal

fora Retorna `TRUE` se o mapeamento de endereço está habilitado.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Os pós-processadores executáveis às vezes atualizam o executável. DIA contém um mecanismo para dar suporte à tradução de símbolos para o novo layout.

 Os aplicativos cliente podem definir o mapa de endereços para uma sessão específica obtendo a interface [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) da interface [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e chamando o método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) seguido por uma chamada para o método [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) . O `get_addressMapEnabled` método retorna os resultados da chamada do `put_addressMapEnabled` método.

## <a name="see-also"></a>Consulte também
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)