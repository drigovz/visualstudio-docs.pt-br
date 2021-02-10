---
title: Função CvWriteMessage | Microsoft Docs
description: Consulte informações de referência para a função do SDK do Visualizador de simultaneidade CvWriteMessage (biblioteca C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteMessageW
- cvmarkers/CvWriteMessageExW
- cvmarkers/CvWriteMessageVA
- cvmarkers/CvWriteMessageExVW
- cvmarkers/CvWriteMessageExA
- cvmarkers/CvWriteMessageA
- cvmarkers/CvWriteMessageExVA
- cvmarkers/CvWriteMessageVW
helpviewer_keywords:
- CvWriteMessageExVA method
- CvWriteMessageW method
- CvWriteMessageVW method
- CvWriteMessageExVW method
- CvWriteMessageExW method
- CvWriteMessageA method
- CvWriteMessageVA method
- CvWriteMessageExA method
ms.assetid: e20ae7be-bfa7-437a-b8c1-fa0f1baa7f83
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e6b3724f3633ce03474ee9915b8d1a4b43a3d46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948121"
---
# <a name="cvwritemessage-function"></a>Função CvWriteMessage
Grava uma mensagem para o arquivo de rastreamento da Visualização Simultânea.

## <a name="syntax"></a>Sintaxe

```C
HRESULT CvWriteMessageW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteMessageA(
    PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteMessageVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteMessageVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteMessageExW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteMessageExA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteMessageExVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteMessageExVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>Parâmetros
 `argList` Lista de argumentos.

 `category` Categoria do período

 `level` Nível de prioridade do período.

 `pMarkerSeries` Contexto de série de marcador válido. Não pode ser NULL.

 `pMessage` Cadeia de formato da mensagem. Não pode ser NULL.

## <a name="return-value"></a>Valor retornado
 S_OK quando a mensagem é gravada com êxito. Código de erro em caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkers.h*

 **Unicode:** CvWriteMessageW, CvWriteMessageVW, CvWriteMessageExW, CvWriteMessageExVW

 **ANSI:** CvWriteMessageA, CvWriteMessageVA, CvWriteMessageExA, CvWriteMessageExVA

## <a name="see-also"></a>Confira também
- [Referência da biblioteca C++](../profiling/cpp-library-reference.md)