---
title: Função CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e50e0d109ac5cfd17c5913213c4b86b406927593
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967648"
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
 `ppProvider`  
 Endereço da variável de objeto do provedor. O endereço não pode ser NULL; a variável pode ter qualquer valor.  
  
 `ppMarkerSeries`  
 Endereço da variável de objeto de série de marcador. O endereço não pode ser NULL; a variável pode ter qualquer valor.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK quando o provedor e a série de marcador são criados com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** *cvmarkers.h*  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)