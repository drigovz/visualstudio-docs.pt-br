---
title: IDiaLineNumber::get_columnNumberEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f2ea924ffd92b6e099302c1bb8e2857dab47479
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855756"
---
# <a name="idialinenumberget_columnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Recupera o número da coluna de origem baseada em um onde a expressão ou instrução termina.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna o número da coluna onde a expressão ou instrução termina. Se o valor for zero, as informações de término da coluna não estão presentes.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O valor da coluna retornado por esse método é um deslocamento de byte na linha até a posição após o último caractere da instrução na linha.

## <a name="see-also"></a>Consulte também
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)