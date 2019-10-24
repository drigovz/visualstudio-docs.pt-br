---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741111"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Retorna todos os valores de marca do ponteiro de aceleração que correspondem a uma função de C++ stub do amp Accelerator.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parâmetros
 `cnt`

no O tamanho da matriz de saída `pPointerTags`.

 `pcnt`

fora A contagem de marcas do ponteiro do acelerador na função de stub do C++ acelerador de amp.

 `pPointerTags`

fora Um ponteiro de matriz `DWORD` que é preenchido com os valores de marca do ponteiro C++ de acelerador na função de stub do acelerador de amp.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado em uma interface `IDiaSymbol` que corresponde a uma C++ função de stub do amp Accelerator.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)