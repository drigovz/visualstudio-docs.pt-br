---
title: Função CvReleaseMarkerSeries | Microsoft Docs
description: Consulte informações de referência para a função do SDK do Visualizador de simultaneidade CvReleaseMarkerSeries (biblioteca C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 60a216c99e21d76efd4d348fea0d06d4f016db5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948238"
---
# <a name="cvreleasemarkerseries-function"></a>Função CvReleaseMarkerSeries
Libera a série de marcador. Não use um objeto de série de marcador após a liberação; caso contrário, o aplicativo poderá falhar. A falha ao liberar a série de marcador causa uma perda de memória.

## <a name="syntax"></a>Sintaxe

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parâmetros
 `pMarkerSeries` Endereço da variável de objeto do provedor. O endereço não pode ser NULL; a variável pode ter qualquer valor.

## <a name="return-value"></a>Valor retornado
 S_OK quando a série de marcador é liberada com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkers.h*

## <a name="see-also"></a>Confira também
- [Referência da biblioteca C++](../profiling/cpp-library-reference.md)