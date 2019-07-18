---
title: Construtor marker_series::marker_series | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b42058e0501612acbf454df725a9f1631489d26e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155297"
---
# <a name="markerseriesmarkerseries-constructor"></a>Construtor marker_series::marker_series
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicializa uma nova instância da classe `marker_series`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `_SeriesName`  
 O nome da série a ser criada.  
  
 `_ProviderGuid`  
 O GUID do provedor da série.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Veja também  
 [Classe marker_series](../profiling/marker-series-class.md)
