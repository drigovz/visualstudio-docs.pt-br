---
title: Função CvLeaveSpan | Microsoft Docs
description: Consulte informações de referência para a função do SDK do Visualizador de simultaneidade CvLeaveSpan (biblioteca C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1dcd98a8233f8080d03650c3989805ee9ec7289
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686578"
---
# <a name="cvleavespan-function"></a>Função CvLeaveSpan
Marca o fim do intervalo.

## <a name="syntax"></a>Sintaxe

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Parâmetros
 `pSpan` Objeto de período retornado pela chamada anterior a CvEnterSpan*. Não pode ser NULL.

## <a name="return-value"></a>Valor retornado
 S_OK quando a mensagem é gravada com êxito. Código de erro em caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkers.h*

## <a name="see-also"></a>Consulte também
- [Referência da biblioteca C++](../profiling/cpp-library-reference.md)