---
title: Função CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs
description: Consulte informações de referência para a função do SDK do Visualizador de simultaneidade CvCreateDefaultMarkerSeriesOfDefaultProvider (biblioteca C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0802b91bb9cbbbe31cb156104bb7b5df3fda1282
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686175"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Função CvCreateDefaultMarkerSeriesOfDefaultProvider
Cria a série de marcador padrão de um provedor padrão.

## <a name="syntax"></a>Sintaxe

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parâmetros
 `ppProvider` Endereço da variável de objeto do provedor. O endereço não pode ser NULL; a variável pode ter qualquer valor.

 `ppMarkerSeries` Endereço da variável de objeto de série de marcador. O endereço não pode ser NULL; a variável pode ter qualquer valor.

## <a name="return-value"></a>Valor retornado
 S_OK quando o provedor e a série de marcador são criados com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkers.h*

## <a name="see-also"></a>Consulte também
- [Referência da biblioteca C++](../profiling/cpp-library-reference.md)