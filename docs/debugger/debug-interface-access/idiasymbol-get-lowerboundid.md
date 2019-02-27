---
title: IDiaSymbol::get_lowerBoundId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBoundId method
ms.assetid: 12ce98e9-a225-4947-88c9-5fda39dd67e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c591b9350128a425a3f97363cb43c43de2005156
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598278"
---
# <a name="idiasymbolgetlowerboundid"></a>IDiaSymbol::get_lowerBoundId
Recupera o identificador de símbolo do limite inferior de uma dimensão de matriz FORTRAN.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_lowerBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

[out] Retorna a ID de símbolo do símbolo que representa o limite inferior de uma dimensão de matriz FORTRAN.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="remarks"></a>Comentários
 O identificador é um valor exclusivo criado pelo SDK do DIA para marcar todos os símbolos como exclusivo.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)