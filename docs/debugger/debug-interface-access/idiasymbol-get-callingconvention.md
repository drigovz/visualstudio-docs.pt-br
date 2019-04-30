---
title: IDiaSymbol::get_callingConvention | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_callingConvention method
ms.assetid: 355d3877-b6b6-45fd-a1d8-baed428d8f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9865d917e24abf58bdcf63e8abb21370f223aad2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402308"
---
# <a name="idiasymbolgetcallingconvention"></a>IDiaSymbol::get_callingConvention
Retorna um indicador de uma convenção de chamada de métodos.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_callingConvention ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
 `pRetVal`

[out] Retorna um valor da [enumeração CV_call_e](../../debugger/debug-interface-access/cv-call-e.md) convenção de chamada de enumeração que especifica um método.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="requirements"></a>Requisitos

|Requisito|Descrição|
|-----------------|-----------------|
|Cabeçalho:|dia2.h|
|Versão:|DIA SDK v7.0|

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeração CV_call_e](../../debugger/debug-interface-access/cv-call-e.md)