---
title: IDiaFrameData::get_lengthLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthLocals method
ms.assetid: 51fe15c3-4cd6-4a06-8a41-a56502209762
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 956a4bc951bfb69d7c36c72a81cde45df9a3e2b8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855917"
---
# <a name="idiaframedataget_lengthlocals"></a>IDiaFrameData::get_lengthLocals
Recupera o número de bytes de variáveis locais enviadas por push na pilha.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_lengthLocals ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna o número de bytes de variáveis locais.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O valor retornado por esse método normalmente é usado na interpretação de uma cadeia de caracteres de programa (consulte o método [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) para a definição de uma cadeia de caracteres de programa).

## <a name="see-also"></a>Consulte também
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)