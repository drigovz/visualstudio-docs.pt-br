---
title: Função CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb0ab16dcd7e42a496317f4e7589bafdbdaf83dc
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54770877"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Função CvCreateDefaultMarkerSeriesOfDefaultProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cria a série de marcador padrão de um provedor padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
## <a name="return-value"></a>Valor de retorno  
 S_OK quando o provedor e a série de marcador são criados com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)
