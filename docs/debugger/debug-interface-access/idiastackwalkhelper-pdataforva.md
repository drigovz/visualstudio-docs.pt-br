---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d150e777f657fcf63dc66dbe3e686c1b445dd473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863805"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Retorna o bloco de dados PDATA associado ao endereço virtual.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parâmetros
 `va`

no Especifica o endereço virtual dos dados a serem obtidos.

 `cbData`

no O tamanho dos dados em bytes a serem obtidos.

 `pcbData`

fora Retorna o tamanho real dos dados em bytes que foram obtidos.

 `pbData`

[entrada, saída] Um buffer que é preenchido com os dados solicitados. Não pode ser `NULL`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum pData para o endereço especificado. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O PDATA (a seção denominada ". pData") de um compiland contém informações sobre a manipulação de exceção para funções.

 O chamador sabe a quantidade de dados a ser retornada para que o chamador não precise solicitar a quantidade de dados disponível. Portanto, é aceitável que uma implementação desse método retorne um erro se o `pbData` parâmetro for `NULL` .

## <a name="see-also"></a>Consulte também
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)