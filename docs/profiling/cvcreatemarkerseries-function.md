---
title: Função CvCreateMarkerSeries | Microsoft Docs
description: Consulte informações de referência para a função do SDK do Visualizador de simultaneidade CvCreateMarkerSeries (biblioteca C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941028"
---
# <a name="cvcreatemarkerseries-function"></a>Função CvCreateMarkerSeries
Cria a série de marcador para determinado provedor.

## <a name="syntax"></a>Sintaxe

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>Parâmetros
 `pProvider` Objeto do provedor inicializado anteriormente por CvInitProvider. Não pode ser NULL.

 `pSeriesName` Nome da série de marcador. Não pode ser NULL, mas uma cadeia de caracteres vazia é permitida.

 `ppMarkerSeries` Endereço de uma variável de saída que armazenará o contexto de série de marcador. Não pode ser NULL.

## <a name="return-value"></a>Valor retornado
 S_OK quando a série de marcador é criada com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Confira também
- [Referência da biblioteca C++](../profiling/cpp-library-reference.md)