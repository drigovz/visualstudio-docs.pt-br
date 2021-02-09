---
title: IDiaLineNumber::get_compilandId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compilandId method
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 30e944c04eb3a6fb7fd7bcc2a7749edbb4d9f2f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855749"
---
# <a name="idialinenumberget_compilandid"></a>IDiaLineNumber::get_compilandId
Recupera um identificador exclusivo para o compiland que contribuiu para esta linha.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_compilandId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

fora Retorna `DWORD` que contém o identificador exclusivo para o compiland que contribuiu para esta linha.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)