---
title: IDiaInjectedSource::get_sourceCompression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 480a0949cd1d42c60b05c5efc89f42c3457ab602
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855777"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Recupera o indicador da compactação de origem usada.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna o indicador da compactação de origem usada. Um valor de zero indica que nenhuma compactação de origem foi usada.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O valor retornado por esse método é específico para o compilador usado. Por exemplo, um compilador pode usar Run-Length codificação ou a compactação estilo Huffman.

## <a name="see-also"></a>Consulte também
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)